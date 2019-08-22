<template>
  <div id="converterRGB" class="converterrgb">
    <div class="color-content" :style="'backgroundColor: rgba('+red+','+green+','+blue+','+alpha+'%)'" @click="setColor(hex)">
        <br>
        <span>
        {{hex}}
        </span>
    </div>
    <div class="slider">
      <span>red:{{red}} </span>
      <input type="range" v-model="red" min="0" max="255" @mouseup="RGBA2HexA">
      <span>green: {{green}} </span>
      <input type="range" v-model="green" min="0" max="255" @mouseup="RGBA2HexA">
      <span>blue: {{blue}}</span>
      <input type="range" v-model="blue" min="0" max="255" @mouseup="RGBA2HexA">
      <span>alpha: {{alpha}} </span>
      <input type="range" v-model="alpha" min="0" max="100" @mouseup="RGBA2HexA">
        <!-- hex: {{hex}} -->
    </div>
  </div>
</template>

<script>
export default {
    name:'converterRGB',
    data(){
        return {
            red:0,
            green:0,
            blue:0,
            alpha:100,
            hex:''
        }
    },
    methods:{
        setColor () {
            this.$emit('setColor', this.hex);
        },
        cRGB2HEX(){
            let r = this.red
            let g = this.green
            let b = this.blue
            this.fullColorHex(r,g,b)
        },
        rgb2Hex (val) { 
            var hex = Number(val).toString(16);
                if (hex.length < 2) {
                    hex = "0" + hex;
                }
                return hex;
        },
        fullColorHex (r,g,b) {   
            var r = this.rgb2Hex(r);
            var g = this.rgb2Hex(g);
            var b = this.rgb2Hex(b);
            if (isNaN(r)&&isNaN(g)&&isNaN(b)) {
                this.hex = 'invalid value'
            } else {
                this.hex = `#${r}${g}${b}`;
            }
        },
        RGBA2HexA() {
            let r = this.rgb2Hex(this.red)
            let g = this.rgb2Hex(this.green)
            let b = this.rgb2Hex(this.blue)
            let a = this.transparentHEX(Number(this.alpha))
            this.hex = `#${r}${g}${b}${a}`
        },
        transparentHEX(val){
            switch (val) {
            case 100:
                return "ff";
            break;
            case 99: 
                return 'FC'
            break;
            case 98: 
                return 'FA'
            break;
            case 97: 
                return 'F7'
            break;
            case 96: 
                return 'F5'
            break;
            case 95: 
                return 'F2'
            break;
            case 94: 
                return 'F0'
            break;
            case 93: 
                return 'ED'
            break;
            case 92: 
                return 'EB'
            break;
            case 91: 
                return 'E8'
            break;
            case 90: 
                return 'E6'
            break;
            case 89: 
                return 'E3'
            break;
            case 88: 
                return 'E0'
            break;
            case 87: 
                return 'DE'
            break;
            case 86: 
                return 'DB'
            break;
            case 85: 
                return 'D9'
            break;
            case 84: 
                return 'D6'
            break;
            case 83: 
                return 'D4'
            break;
            case 82: 
                return 'D1'
            break;
            case 81: 
                return 'CF'
            break;
            case 80: 
                return 'CC'
            break;
            case 79: 
                return 'C9'
            break;
            case 78: 
                return 'C7'
            break;
            case 77: 
                return 'C4'
            break;
            case 76: 
                return 'C2'
            break;
            case 75: 
                return 'BF'
            break;
            case 74: 
                return 'BD'
            break;
            case 73: 
                return 'BA'
            break;
            case 72: 
                return 'B8'
            break;
            case 71: 
                return 'B5'
            break;
            case 70: 
                return 'B3'
            break;
            case 69: 
                return 'B0'
            break;
            case 68: 
                return 'AD'
            break;
            case 67: 
                return 'AB'
            break;
            case 66: 
                return 'A8'
            break;
            case 65: 
                return 'A6'
            break;
            case 64: 
                return 'A3'
            break;
            case 63: 
                return 'A1'
            break;
            case 62: 
                return '9E'
            break;
            case 61: 
                return '9C'
            break;
            case 60: 
                return '99'
            break;
            case 59: 
                return '96'
            break;
            case 58: 
                return '94'
            break;
            case 57: 
                return '91'
            break;
            case 56: 
                return '8F'
            break;
            case 55: 
                return '8C'
            break;
            case 54: 
                return '8A'
            break;
            case 53: 
                return '87'
            break;
            case 52: 
                return '85'
            break;
            case 51: 
                return '82'
            break;
            case 50: 
                return '80'
            break;
            case 49: 
                return '7D'
            break;
            case 48: 
                return '7A'
            break;
            case 47: 
                return '78'
            break;
            case 46: 
                return '75'
            break;
            case 45: 
                return '73'
            break;
            case 44: 
                return '70'
            break;
            case 43: 
                return '6E'
            break;
            case 42: 
                return '6B'
            break;
            case 41: 
                return '69'
            break;
            case 40: 
                return '66'
            break;
            case 39: 
                return '63'
            break;
            case 38: 
                return '61'
            break;
            case 37: 
                return '5E'
            break;
            case 36: 
                return '5C'
            break;
            case 35: 
                return '59'
            break;
            case 34: 
                return '57'
            break;
            case 33: 
                return '54'
            break;
            case 32: 
                return '52'
            break;
            case 31: 
                return '4F'
            break;
            case 30: 
                return '4D'
            break;
            case 29: 
                return '4A'
            break;
            case 28: 
                return '47'
            break;
            case 27: 
                return '45'
            break;
            case 26: 
                return '42'
            break;
            case 25: 
                return '40'
            break;
            case 24: 
                return '3D'
            break;
            case 23: 
                return '3B'
            break;
            case 22: 
                return '38'
            break;
            case 21: 
                return '36'
            break;
            case 20: 
                return '33'
            break;
            case 19: 
                return '30'
            break;
            case 18: 
                return '2E'
            break;
            case 17: 
                return '2B'
            break;
            case 16: 
                return '29'
            break;
            case 15: 
                return '26'
            break;
            case 14: 
                return '24'
            break;
            case 13: 
                return '21'
            break;
            case 12: 
                return '1F'
            break;
            case 11: 
                return '1C'
            break;
            case 10: 
                return '1A'
            break;
            case 9: 
                return '17'
            break;
            case 8: 
                return '14'
            break;
            case 7: 
                return '12'
            break;
            case 6: 
                return '0F'
            break;
            case 5: 
                return '0D'
            break;
            case 4: 
                return '0A'
            break;
            case 3: 
                return '08'
            break;
            case 2: 
                return '05'
            break;
            case 1: 
                return '03'
            break;
            case 0: 
                return '00'
            break;
            }
        }
    },
    created(){
        this.cRGB2HEX()
    }
}
</script>

<style>
.converterrgb {
    /* position: fixed; */
    margin: 10px 50px 10px auto;
}
.converterrgb  .color-content{
    margin: 10px auto 10px auto;
    height:100px;
    width:200px;
    border-radius: 5%;
}
.converterrgb  .color-content span {
    padding: 5px;
    /* background-color: rgba(60, 60, 60, 0.578); */
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #f0fff45f;
}
 .converterrgb .slider{
    position: relative;
    margin: 10px auto 10px auto;
    width: 250px;
    height: 10px;
    display: flex;
    flex-direction: column;
    color: #231a1a
}

</style>