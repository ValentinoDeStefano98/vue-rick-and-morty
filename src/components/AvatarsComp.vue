<template>
    <div class="row">
        <CardAvatar
        v-for="(element, index) in avatarsArray"
        :key="index"
        :image="element.image"
        :name="element.name"
        :species="element.species"
        :origin="element.origin"
        />
    </div>
</template>

<script>

import axios from 'axios';
import CardAvatar from './partials/CardAvatar.vue'

export default {
    name:'AvatarsComp',
    components: {
        CardAvatar
    },
    data(){
        return{
            avatarsArray: []
        }
    },
    created(){
        axios.get('https://api.sampleapis.com/rickandmorty/characters')
            .then((res) => {
                console.log(res.data);
                this.avatarsArray = res.data;
            })
            .catch ((error) => {
                console.log(error)
            })
    }
}

</script>

<style scoped lang="scss">

</style>