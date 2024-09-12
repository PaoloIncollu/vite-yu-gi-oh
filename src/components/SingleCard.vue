<script>
export default {
  props: {

    card: Object,
    
  }
}
</script>

<template>
  
    <div class="card">

        <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.name">

        <div class="card-body">

            <h3 class="text-center">

                {{ card.name}}

            </h3>

            <h5 class="text-center">

                {{ card.archetype}}

            </h5>

        </div>

    </div>
  
</template>

<style lang="scss" scoped>

.card{

    .card-body{
        
        background-color: $bg-main;
        min-height: 150px;

    }

}

</style>