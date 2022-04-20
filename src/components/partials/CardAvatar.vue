<template>
    <div class="col-3">
        <img :src="image" alt="immagine avatar" class="rounded-circle">
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

</style>
