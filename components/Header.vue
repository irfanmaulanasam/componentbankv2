<template>
  <div id="HeaderNav">
    <header>
      <section id="show-modal" @click="showModal = true">
        <h3>Color<span>Picker</span><sup>v 1.0</sup></h3>
      </section>
      <modal v-if="showModal" 
        :header="'ini header kiriman dari headerNav'"
        :body="'ini body kiriman dari headerNav'"
        :footer="'ini footer kiriman dari headerNav'"
        @close="showModal = false">
      </modal>
      <div class="background-profile" @click="changeColor" :style="'background:'+color.back">
        <div class="foreground-profile" :style="'background:'+color.fore"></div>
      </div>
    </header>
  </div>
</template>

<script>
import modal from './modal'
export default {
  name: 'HeaderNav',
  props:{
    color:{
      type:Object,
      required:true
    },
  },
  data(){
    return{
      coloring:null,
      showModal:false
    }
  },
  methods:{
    changeColor(){
      this.coloring = this.color.fore
      this.color.fore = this.color.back
      this.color.back = this.coloring
      console.log(this.color.fore, this.color.back, this.coloring)
    },
  }
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 60px;
  background: #171717;
  padding: 0px 15px;
}
h3 {
  color: #F3F3F3;
  font-size: 28px;
  font-weight: 300;
  text-transform: uppercase;
}

h3 span {
  color: #FFCE00;
  font-weight: 900;
}
h3 sup {
  color: #ff0000;
  font-weight: 500;
  font-size: 15px;
}

.background-profile {
  margin-right: 10px;
  margin-bottom: 15px;
  padding: 20px;
  border-radius: 5%;
  border: 2px solid #7e7e7e;
}

.foreground-profile {
  border: 2px solid #7e7e7e;
  position: absolute;
  padding: 15px;
  border-radius: 5%;
}

</style>