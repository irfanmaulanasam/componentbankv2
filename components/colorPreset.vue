<template>
  <div class="color-preset">
    <div v-if="selectedColor" >
      <colorPicker :colors="selectedColor.variation" @setColor="setColor"/>
    </div>
      select theme : <select v-model="selectedColor" class="custom-select" placeholder="add themed color">
        <option v-for="(option,i) in colorPreset" :key="i" :value="option" :style="'background:'+option.variation[0] " aria-hidden="true">
          <!-- <div class="color" :style="'background:'+option.variation[0]" > </div> -->
            {{ option.name }}
        </option>
      </select>
  </div>
</template>

<script>
import colorPicker from "@/components/ColorPicker"
export default {
  name: 'color-preset',
  components:{
      colorPicker
  },
  props: {
    colorPreset:{
      type:Array,
    }
  },
  data(){
      return {
          selectedColor:""

      }
  },
  methods: {
    setColor (color) {
      this.$emit('setColor', color);
    },
    setColorProperty(color){
      if (this.selectedColorName) {
        console.log(color)
        return color.splice(0,1)
      }
    }
  },
}
</script>

<style scoped>
ul{
  list-style: none;
  display: inline;
  margin: 1px dashed red;
}
.color {
  border: 1px solid #AAA;
  height: 20px;
  width: 20px;
}

select {

  /* styling */
  background-color: white;
  border-bottom: thin solid #919191;
  border-radius: 4px;
  display: inline-block;
  font: inherit;
  line-height: 1.5em;

  /* reset */

  margin: 0;      
  -webkit-box-sizing: border-box;
  -moz-box-sizing: border-box;
  box-sizing: border-box;
  -webkit-appearance: none;
  -moz-appearance: none;
}


/* arrows */

select.classic {
  background-image:
    linear-gradient(45deg, transparent 50%, blue 50%),
    linear-gradient(135deg, blue 50%, transparent 50%),
    linear-gradient(to right, skyblue, skyblue);
  background-position:
    calc(100% - 20px) calc(1em + 2px),
    calc(100% - 15px) calc(1em + 2px),
    100% 0;
  background-size:
    5px 5px,
    5px 5px,
    2.5em 2.5em;
  background-repeat: no-repeat;
}

select.classic:focus {
  background-image:
    linear-gradient(45deg, white 50%, transparent 50%),
    linear-gradient(135deg, transparent 50%, white 50%),
    linear-gradient(to right, gray, gray);
  background-position:
    calc(100% - 15px) 1em,
    calc(100% - 20px) 1em,
    100% 0;
  background-size:
    5px 5px,
    5px 5px,
    2.5em 2.5em;
  background-repeat: no-repeat;
  border-color: grey;
  outline: 0;
}




</style>

