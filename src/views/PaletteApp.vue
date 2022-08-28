<template>
  <h1>Vue palette</h1>
  <div class="app">
    <div
      class="palette"
      v-on:mousemove="changeColor"
      v-on:click="pickColor"
      v-bind:style="paletteStyle"
    ></div>
    <p>rgba( {{ yellow }}, {{ green }}, 200, 0.5 )</p>

    <img
      class="pallete-image"
      src="https://www.dainippon-tosho.co.jp/star/special/sky/images/sky_02_3_sp.png"
      alt="パレット背景"
    />
    <img
      class="miniPalette-image"
      src="https://s3-ap-northeast-1.amazonaws.com/sekaido-store-image-production/product_images/14142/product/sku_2042319929465_1.jpg?1507012576"
      alt="パレット画像"
    />

    <div class="colors-container">
      <h2>[ミニパレット]</h2>
      <div
        class="mini-palette"
        v-for="(color, index) in colors"
        v-bind:key="index"
        v-bind:style="{
          backgroundColor: `raba(${color.yellow}, ${color.green}, 200, 0.5)`,
        }"
        v-on:click="showColor(color)"
      ></div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      yellow: 200,
      green: 200,
      colors: [],
    }
  },
  methods: {
    //マウスの位置に応じて色を変える
    changeColor(e) {
      this.yellow = e.offsetX
      this.green = e.offsetY
    },
    //色を選んでミニパレットに追加する
    pickColor() {
      const newColor = {
        yellow: this.yellow,
        green: this.green,
      }
      this.colors.push(newColor)
    },
    //パレットに指定した色を表示する
    showColor(color) {
      this.yellow = color.yellow
      this.green = color.green
    },
  },
  computed: {
    paletteStyle() {
      return {
        backgroundColor: `rgba(${this.yellow}, ${this.green}, 200, 0.5)`,
      }
    },
  },
}
</script>

<style>
.h1 {
  font-family: "fantacy";
}
.pallete-image {
  position: absolute;
  width: 110%;
  height: 150%;
  opacity: 0.4;
  z-index: 1;
}

.app {
  display: flex;
  width: 100%;
  flex-direction: column;
  align-items: center;
}
.palette {
  position: center;
  width: 500px;
  height: 400px;
  z-index: 2;
}
.h2 {
  font-family: "fantacy";
}

.mini-palette {
  position: relative;
  min-width: 50px;
  height: 50px;
  z-index: 4;
}
.colors-container {
  position: relative;
  top: auto;
  width: 300px;
  padding-top: 8px;
}
.miniPalette-image {
  position: bottom;
  width: 30%;
  height: 10%;
  z-index: 3;
  opacity: 0.9;
}
</style>
