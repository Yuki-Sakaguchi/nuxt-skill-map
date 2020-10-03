<template>
  <div class="wrapper">
    <div
      v-for="(matrixText, index) in matrix"
      :key="matrixText"
      :class="'matrix matrix--' + (index + 1)"
    >
      {{ matrixText }}
    </div>
    <VueDragResize
      v-for="(item, index) in items"
      :key="item.text"
      :is-active="true"
      :is-resizable="false"
      class="drag-item"
      :w="getTextLengthSize(item.text.length)"
      :h="50"
      :min-w="100"
      :min-h="50"
      :x="parentWidth / 2 - getTextLengthSize(item.text.length) / 2"
      :y="parentHeight / 2 + index * 55 - (items.length * 55) / 2"
      :parent-w="parentWidth"
      :parent-h="parentHeight"
      :parent-limitation="true"
      :style="{ color: item.textColor, backgroundColor: item.color }"
      @:dragging="resize"
    >
      {{ item.text }}
    </VueDragResize>
  </div>
</template>

<script>
import VueDragResize from 'vue-drag-resize'

export default {
  components: {
    VueDragResize,
  },
  data() {
    return {
      width: 0,
      height: 0,
      top: 0,
      left: 0,
      parentWidth: window.innerWidth,
      parentHeight: window.innerHeight - 64,
      matrix: ['好き', '嫌い', '得意', '苦手'],
      items: [
        {
          text: 'javascript',
          color: '#4fd0ca',
          textColor: 'white',
        },
        {
          text: 'html',
          color: '#4fd0ca',
          textColor: 'white',
        },
        {
          text: 'css',
          color: '#4fd0ca',
          textColor: 'white',
        },
        {
          text: 'long long long long long long name item',
          color: '#4fd0ca',
          textColor: 'white',
        },
        {
          text: 'design',
          color: '#4fd0ca',
          textColor: 'white',
        },
      ],
    }
  },
  methods: {
    resize(newRect) {
      this.width = newRect.width
      this.height = newRect.height
      this.top = newRect.top
      this.left = newRect.left
    },
    getTextLengthSize(size) {
      const width = size * 10
      if (width < 100) {
        return 100
      }
      return width
    },
  },
}
</script>

<style lang="scss" scoped>
.wrapper {
  position: relative;
  width: 100%;
  height: 100%;
  z-index: 2;
  &::before,
  &::after {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    margin: auto;
  }
  &::before {
    width: 70%;
    height: 1px;
    background-color: rgba(black, 0.5);
    z-index: -1;
  }
  &::after {
    height: 70%;
    width: 1px;
    background-color: rgba(black, 0.5);
    z-index: -1;
  }
}

.drag-item {
  display: flex;
  justify-content: center;
  align-items: center;
  &::before {
    outline: none;
  }
}

.matrix {
  position: absolute;
  margin: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 20px;
  font-weight: bold;
  &--1 {
    top: 10px;
    right: 0;
    left: 0;
  }
  &--2 {
    bottom: 10px;
    right: 0;
    left: 0;
  }
  &--3 {
    top: 0;
    bottom: 0;
    right: 10px;
  }
  &--4 {
    top: 0;
    bottom: 0;
    left: 10px;
  }
}
</style>
