<template>
  <div id="app">
    <div class="model">
      <img
        :style="{transform:`rotate(${deg}deg) scale(${scaleVal})`}"
        src="https://fengyuanchen.github.io/viewerjs/images/tibet-1.jpg"
      >
      <ul class="toolbar">
        <li @click="scale('extend')">放大</li>
        <li @click="scale('shrink')">缩小</li>
        <li @click="rotate">旋转</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      deg: 0,
      scaleVal: 0
    };
  },
  methods: {
    rotate() {
      this.deg += 90;
      if (this.deg >= 360) {
        this.deg = 0;
      }
    },

    scale(type) {
      if (type === "extend") {
        this.scaleVal += 0.5;
      } else {
        this.scaleVal -= 0.5;
      }
    }
  }
};
</script>

<style>
ul,
li {
  list-style-type: none;
}
.model {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
}
.img {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  margin: auto;
  transition: all 1s ease;
}
.toolbar {
  position: absolute;
  bottom: 20px;
  left: 50%;
  z-index: 99999;
  transform: translateX(-50%);
  overflow: hidden;
  background: red;
}
.toolbar > li {
  float: left;
  margin: 0 20px;
}
</style>
