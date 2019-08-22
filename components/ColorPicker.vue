<template>
  <div class="color-picker">
    <div 
      class="color"
      v-for="(color, i) in colors"
      :key="i"
      :style="'background:'+color"
      @click="setColor(color)"/>
  </div>
</template>

<script>
export default {
  name: 'color-picker',
  props: {
    colors:{
      type:Array,
    }
  },
  methods: {
    setColor (color) {
      this.$emit('setColor', color);
    },
    setSecondColor (color) {
      this.$emit('setSecondColor', color);
    }
  }
}
</script>

<style scoped>
.color-picker {
  /* position: absolute; */
  width: 275px;
  display: grid;
  /* margin: 15px auto; */
  grid-template-columns: repeat(11, 25px);
}
.color {
  border: 1px solid #AAA;
  height: 25px;
}
</style>

