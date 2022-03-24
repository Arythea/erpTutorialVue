<template>
    <div>
        <img v-if="active" :src="img" class="fake-background">
        <div class="container">
            <div class="row" v-if="active">
                <div class="col-6 mx-auto">
                    <div class="alert"><h2>Tutorial</h2></div>
                    <ButtonComp @moveScene="runMoveScene" labelProp="Anterior" />
                    <ButtonComp @moveScene="runMoveScene" labelProp="Següent" />
                    <EscenaComp :textsProp="texts.map( x => x.txt )" :currentSentenceProp="currentSentence" />
                </div>
            </div>
            <div class="row" v-else>
                <div class="col-6 mx-auto welcome">
                    <h1>Benvingut/da</h1>
                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Quo vitae quod nulla consequatur, odit aperiam. Ducimus, nobis. Sapiente necessitatibus ad quas, a ullam quasi incidunt hic aperiam eligendi. Esse, porro!</p>
                    <button @click="start">Començar</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import EscenaComp from '@/components/EscenaComp.vue'
import ButtonComp from '@/components/ButtonComp.vue'
import texts from '@/assets/texts.js'
export default {
  name: 'HomeComp',
  components: {
    EscenaComp,
    ButtonComp
  },
  data(){
      return {
          img: require('@/assets/1.jpg'),
          texts: texts,
          currentSentence: 0,
          active: false
      }
  },
  methods: {
      runMoveScene(label) {
          if(label == 'Anterior') {
              this.currentSentence--;
          } else {
              this.currentSentence++;
          }
      },
      start() {
          this.active = !this.active;
      }
  },
  watch: {
      currentSentence: function (val) {
          if (val == -1) this.currentSentence = this.texts.length - 1;
          if (val == this.texts.length) this.currentSentence = 0;
          this.img = require(`@/assets/${this.currentSentence + 1}.jpg`);
      }
  }
}
</script>

<style scoped>
    .fake-background {
        position: absolute;
        width: 100%;
        top: 0;
        left: 0;
    }
    button {
        position: relative;
    }
    .alert {
        background-color: rgba(100,255,255,0.7);
    }
</style>