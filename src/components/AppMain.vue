<script>

import SingleCard from './SingleCard.vue';
import { store } from '../store.js';

export default {
  data() {
    return {  
      store
    }
  },
 
  components:{

	SingleCard

  },
  methods: {
    searchArchetype(){
		
		
		this.$emit('searchArchetype')
		
	}
  }
}

</script>

<template>

	<main>

		
	<div class="container-select-arc">

		<div>
			<label for="search" class="form-label fs-2">Seleziona il tipo di carte che vuoi visualizzare</label>
			<select  id="search" v-model="store.selectArchetype"
			@$emit="searchArchetype()" class="form-select w-25 h-10">

				<option v-for="(archetype,index) in store.allArchetype" :key="index" :value="archetype.archetype_name">{{ archetype.archetype_name }}</option>

			</select>
		</div>
			
	</div>
	
			
		<div class="my-container-row">

			<div class="row p-5 bg-white">

				<div v-for="(card,index) in store.allCard" :key="index" class="col-12 col-sm-6 col-md-3 pb-3 ">

					<SingleCard :card="card"/>

				</div>

			</div>

		</div>

	</main>

</template>

<style lang="scss" scoped>

	main{

		background-color: $bg-main;

		.container-select-arc{

			width: 80%;
			margin: 0 auto;

			.select-arc{

				width: fit-content;
				
				font-size: 30px;
				
				
			}
		}

		.my-container-row{

			width: 80%;
			margin: 0 auto;
			padding: 100px 0 50px;

			.bg-white{

				background-color: white;

			}
		}
	}

</style>
