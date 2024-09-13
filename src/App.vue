<script>
/* 
  Per importare ed utilizzare un componente dentro un altro devo SEMPRE seguire questi 3 passi:
  1) Importazione del componente
  2) Dichiarazione del componente
  3) Utilizzo del componente
*/
// 1) Importazione del componente
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import AppFooter from './components/AppFooter.vue';
import axios from 'axios';
import { store } from './store.js';
export default {
  data() {
    return { 

      store,
      allCard:[],
      allArchetype:[]
    }
  },
  // 2) Dichiarazione del componente
  components: {
    AppHeader,
    AppMain,
    AppFooter
  },
  created() {
    
    this.getDataFromAPi();
     axios
      .get('https://db.ygoprodeck.com/api/v7/archetypes.php')
      .then((arc) => {
        console.log('archetype CREATO DA AXIOS:', arc);
        console.log('DATI  archetype CHE CI HA RISPOSTO IL SERVER:', arc.data);
        this.store.allArchetype = arc.data;
	  
    });
    },

  methods: {
    getDataFromAPi(){

       axios
      .get('https://db.ygoprodeck.com/api/v7/cardinfo.php?',{

        params:{
          archetype:this.store.selectArchetype
        } 
      }).then((res) => {
        
        console.log('OGGETTO CREATO DA AXIOS:', res);
        console.log('DATI CHE CI HA RISPOSTO IL SERVER:', res.data.data);
        this.store.allCard = res.data.data;
	
    }).catch((err) => {
        this.store.ciao = [];
      });
    
  }

}}
</script>

<template>
  <div>
    <!-- 3) Utilizzo del componente -->
    <AppHeader />
    
    <AppMain @searchArchetype="getDataFromApi()"/>

    <AppFooter/>
  </div>
</template>

<style lang="scss">
@use '../src/assets/scss/main.scss' as *;

// Import all of Bootstrap's CSS
@import "bootstrap/scss/bootstrap";
</style>
