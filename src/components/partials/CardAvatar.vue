<template>
    <div class="col-3 text-center my-5">
        <img :src="image" alt="immagine avatar" class="rounded-circle">
        <h3 class="my-3">{{name}}</h3>
        <div class="divider my-3"></div>
        <h4 class="my-3">{{origin}}</h4>
        <span class="fw-bolder my-3">{{species}}</span>
    </div>
    
</template>

<script>
export default {
    name: 'CardAvatar',
    props:{
        image: String,
        name: String,
        species: String,
        origin: String,
    }
}

</script>

<style scoped lang="scss">

.divider{
    width: 30%;
    height: 1px;
    background-color: #1a1a1a;
    margin: 0 auto
}

</style>
