<template>
    <div class="h-screen border-r-4 bg-white" >
        <h1 class="text-3xl text-center pt-3 font-semibold text-cyan-800 leading-loose">Logistics</h1>
        <ul class="list-none capitalize pt-3 flex flex-col justify-center">
            <li @click="emitTabEvent(1)" class="tab" :class="{'bg-blue-500 text-gray-100': active === 1}">home</li>
            <li @click="emitTabEvent(2)" class="tab" :class="{'bg-blue-500 text-gray-100': active === 2}">approve products</li>
            <li @click="emitTabEvent(3)" class="tab" :class="{'bg-blue-500 text-gray-100': active === 3}">product approval</li>
            <li @click="emitTabEvent(4)" class="tab" :class="{'bg-blue-500 text-gray-100': active === 4}">deliver products</li>
            <li @click="emitTabEvent(5)" class="tab" :class="{'bg-blue-500 text-gray-100': active === 5}">product delivery</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Sidebar',
    props: ['active'],
    methods: {
        emitTabEvent(tabID) {
            this.$emit("changetab", tabID)
        }
    }
}
</script>

<style scoped>
    .tab {
        @apply pl-10 text-2xl leading-loose border-b-4 border-gray-300 flex;
    }

    .tab:first-child {
        @apply border-t-4 border-gray-300;
    }

    .tab:hover {
        @apply bg-blue-600 cursor-pointer text-gray-100;
    }
</style>