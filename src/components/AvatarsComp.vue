<template>
    <div>
        <div class="row" v-if="!loadingStatus">
            <CardAvatar
            v-for="(element, index) in avatarsArray"
            :key="index"
            :image="element.image"
            :name="element.name"
            :species="element.species"
            :origin="element.origin"
            />
        </div>  
        <div v-else>
            <LoaderComp/>
        </div>   
    </div>   
</template>

<script>

import axios from 'axios';
import CardAvatar from './partials/CardAvatar.vue'
import LoaderComp from './LoaderComp.vue'

export default {
    name:'AvatarsComp',
    components: {
        CardAvatar,
        LoaderComp
    },
    data(){
        return{
            avatarsArray: [],
            loadingStatus: true
        }
    },
    created(){
        axios.get('https://api.sampleapis.com/rickandmorty/characters')
            .then((res) => {
                console.log(res.data);
                this.avatarsArray = res.data;
                this.loadingStatus = false
            })
            .catch ((error) => {
                console.log(error)
            })
    }
}

</script>

<style scoped lang="scss">

</style>