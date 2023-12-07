<template>
   

    <div v-for="pname of products" :key="pname.id">
            <ProdVuew :pname=pname />
    </div>

</template>

<script>
import ProdVuew from './ProdVuew.vue'

export default{
    name: 'ListVuew',
    props:{
        products: Array
    },
    components:{
        ProdVuew
    }
}

</script>

<style>


</style>