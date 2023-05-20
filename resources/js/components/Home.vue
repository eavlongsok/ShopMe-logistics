<template>
    <h2 class="heading-2 mb-3">Home</h2>
    <div class="flex flex-row justify-evenly flex-wrap gap-5 capitalize">
        <Card title="total deliveries" value="10000" color="red" />
        <Card title="total deliveries" value="10000" color="green" />
        <Card title="total deliveries" value="10000" color="purple" />
        <Card title="total deliveries" value="10000" color="darkblue" />
    </div>

    <!-- <h2 class="heading-2 mt-10 mb-3 inline-block">Product Approval</h2>
    <span class="hover:font-bold hover:underline ml-3 text-sm cursor-pointer" @click="$emit('changetab', 3)">View All</span> -->
</template>

<script>
import Card from './Card.vue';

    export default {
    name: "Home",
    components: { Card },
    emits: ['changetab']
}
</script>

<style scoped>

</style>