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

  }
}

</script>

<template>

	<main>

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
