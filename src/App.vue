<template>
<div>
  <h2>Volume Tracker (0-20)</h2>
 <h3>Current volume - {{ volume }}</h3>
 <div>
    <button class="btn btn-primary" @click="volume += 2">Increment</button>
    <button class="btn btn-primary" @click="volume -= 2">Decrement</button>
</div>
<input type="text" v-model="movie">
<Great/>
<card />

<button @click="activeTabc= 'TabA'">Tab A</button>
<button @click="activeTab= 'TabB'">Tab B</button>
<button @click="activeTab= 'TabC'">Tab C</button>
<!-- <TabA v-if="activeTab === 'TabA' "/>
<TabB v-if="activeTab === 'TabB' "/>
<TabC v-if="activeTab === 'TabC' "/> -->
<component :is="activeTab"/>
</div>

</template>

<script>
import great from './components/Great.vue'
import card from './components/card.vue'
import 'bootstrap/dist/css/bootstrap.css'
import TabA from './components/TabA.vue'
import TabB from './components/TabB.vue'
import TabC from './components/TabC.vue'
export default {
  name: 'App',
  components: {
    great,
    card,
    TabA,
    TabB,
    TabC,
  }, // Ensure this comma is present
  data() {
    return {
      volume: 0,
      movie: '',
      activeTab:'TabA'
    };
  },
  methods:{

  },
  computed:{

  },
  watch:{
    volume(newValue, oldValue){
      if(newValue > oldValue && newValue === 16 ){
        alert('Listening to a high volume for a long time may damage yor hearing')
      }
    }
  },
  movie(newValue){
    console.log('Calling Api movie api value = ${newValue}')
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
