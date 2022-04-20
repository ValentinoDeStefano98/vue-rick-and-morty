<template>
    <header class="container text-center py-4 fw-bolder">
        <h1>{{ msg }}</h1>
    </header>
</template>

<script>
export default {
    name:'HeaderComp',
    props: ['msg']
}

</script>

<style scoped lang="scss">

</style>
