<template>
    <div>
        <Header></Header>
        <Nuxt />
    </div>
</template>

<script>
import Header from '../components/header.vue';
export default {
    name: 'Layout',
    components: Header
}
</script>