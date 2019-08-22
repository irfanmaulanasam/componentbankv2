<template>
  <div id="app">
    <Header :color="color" />
    <converterRGB @setColor="setColor"/>
    <ColorPicker :colors="colors" @setColor="setColor"/>
    default color
    <colorPresetPicker :colorPreset="colorPreset" @setColor="setColor"/>
    <ColorGrid :color="color" />
  </div>
</template>

<script>
import Header from '@/components/Header'
import ColorPicker from '@/components/ColorPicker'
import ColorPresetPicker from '@/components/ColorPreset'
import ColorGrid from '@/components/ColorGrid'
import colorPreset from '@/assets/color.json'
import converter from '@/components/converter'
import converterRGB from '@/components/converterRGB'
export default {
  name: 'app',
  components: {
    Header,
    ColorPicker,
    ColorPresetPicker,
    ColorGrid,
    converter,
    converterRGB
  },
  data () {
    return {
      colorPreset,
      colors: [
        '#4D4D4D', '#999999', '#FFFFFF', '#F44E3B', '#FE9200', '#FCDC00',
        '#DBDF00', '#A4DD00', '#68CCCA', '#73D8FF', '#AEA1FF', '#FDA1FF',
        '#333333', '#808080', '#CCCCCC', '#D33115', '#E27300', '#FCC400',
        '#B0BC00', '#68BC00', '#16A5A5', '#009CE0', '#7B64FF', '#FA28FF',
        '#000000', '#666666', '#B3B3B3', '#9F0500', '#C45100', '#FB9E00',
        '#808900', '#194D33', '#0C797D', '#0062B1', '#653294', '#AB149E'
      ],
      color: {
        fore:'#ffffff',
        back:'#ccc'
        }
    }
  },
  methods: {
    setColor (color) {
      this.color.fore = color
    }
  }
}
</script>

<style>
body {
  margin: 0;
  padding: 0;
  background: #d7cfd2;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #6f6f6f;
}
</style>
