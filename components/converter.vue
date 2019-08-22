<template>
    <div id="converter">
        <input type="text" v-model="hexcolor" placeholder="input hex color here" @keyup="cHEX2RGB(hexcolor)">
        <div class="rgba">
            <input type="text" v-model="rcolor" placeholder="red" @keyup="cRGB2HEX">
            <input type="text" v-model="rcolor" placeholder="green" @keyup="cRGB2HEX">
            <input type="text" v-model="bcolor" placeholder="blue" @keyup="cRGB2HEX">
        </div>
        <div class="rgb-result" :style="'background:'+hexcolor">
            {{rgbresult}}
        </div>
        <div class="hex-result" :style="'background:'+hexresult">
            {{hexresult}}
        </div>
    </div>
</template>

<script>
export default {
    name:'converter',
    data(){
        return {
            hexresult:'',
            rgbresult:'',
            rcolor:'',
            gcolor:'',
            bcolor:'',
            hexcolor:'',
        }
    },
    methods:{
        cHEX2RGB (hex) {
            "use strict";
            if (hex.charAt(0) === '#') {
                hex = hex.substr(1);
            }
            if ((hex.length < 2) || (hex.length > 6)) {
                return false;
            }
            var values = hex.split(''),
                r,
                g,
                b;

            if (hex.length === 2) {
                r = parseInt(values[0].toString() + values[1].toString(), 16);
                g = r;
                b = r;
            } else if (hex.length === 3) {
                r = parseInt(values[0].toString() + values[0].toString(), 16);
                g = parseInt(values[1].toString() + values[1].toString(), 16);
                b = parseInt(values[2].toString() + values[2].toString(), 16);
            } else if (hex.length === 6) {
                r = parseInt(values[0].toString() + values[1].toString(), 16);
                g = parseInt(values[2].toString() + values[3].toString(), 16);
                b = parseInt(values[4].toString() + values[5].toString(), 16);
            } else {
                return false;
            }
            if ((r != null && g!= null  && b !== null )||(!isNaN(r)&&!isNaN(g)&&!isNaN(b)) ) {
                this.rgbresult = [r, g, b]
                } else {
                this.rgbresult = 'invalid value'
            }
        },
        cRGB2HEX(){
            let r = this.rcolor
            let g = this.gcolor
            let b = this.bcolor
            this.fullColorHex(r,g,b)
        },
        rgbToHex (rgb) { 
            var hex = Number(rgb).toString(16);
                if (hex.length < 2) {
                    hex = "0" + hex;
                }
                return hex;
        },
        fullColorHex (r,g,b) {   
            var red = this.rgbToHex(r);
            var green = this.rgbToHex(g);
            var blue = this.rgbToHex(b);
            if (isNaN(red)&&isNaN(green)&&isNaN(blue)) {
                this.hexresult = 'invalid value'
            } else {
                this.hexresult = `#${red}${green}${blue}`;
            }
        }
    },
}
</script>

<style scoped>
input {
    border-bottom: 2px dotted grey;
    border-left-width: 0px;
    border-right-width: 0px;
    border-top-width: 0px;
    background: none;
    width: 50px;
    color: #544a4a;
}
.rgb{
    width: 50px;
}

</style>