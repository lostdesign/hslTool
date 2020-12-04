<template>
  <div class="flex">
    <div>
      <Sketch v-model="colors"/>
      <div class="meta">
        <h1>Current Color</h1>
        <p>{{colors.hex}}</p>
      </div>
    </div> 
    <div class="flex-column">
      <template v-for="lightness in lightnessRange">
        <div class="colorResult" :key="lightness">
          <div class="color-cube" :style="`background-color: hsl(${colors.hsl.h}, ${colors.hsl.s*100}%, ${lightness}%);`"></div>
          <p>hsl({{Math.round(colors.hsl.h)}}, {{Math.round(colors.hsl.s*100)}}%, {{lightness}}%)</p>
        </div>
      </template>
    </div>
  </div>
</template>

<script>
import Sketch from '@/components/sketch/Sketch.vue'

export default {
  data () {
    return {
      colors: {
        hsl: { h: 0, s: 0, l: 0, a: 1 },
        hex: '#000000',
      },
      lightnessRange: [10,20,30,40,50,60,70,80,90]
    }
  },
  components: {
    Sketch
  }
}
</script>

<style>
.flex {
  display:flex;
  width: 100vw;
  height: 100vh;
  align-items:center;
}

.meta {
  margin:10px;
  margin-top: 25px;
}

.meta h1 {
  font-size:18px;
}

.meta p {
  font-size: 12px;
}

.colorResult {
  display: flex;
  flex-direction: column;
}

.flex-column {
  display:flex;
}

.color-cube {
  width: 100%;
  height: 50px;
  margin: 10px;
  border: 1px solid #eee;
  border-radius: .3rem;
}
</style>