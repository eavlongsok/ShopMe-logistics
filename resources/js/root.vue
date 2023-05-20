<template>
    <Login v-if="loggedIn === false"/>
    <div class="mt-16" v-else-if="loggedIn === true">
        <Header :active="active" @logout="loggedIn = false"/>
        <div class="">
            <Sidebar class="fixed w-1/5 z-[1]" :active="active" @changetab="changeTab"/>
            <div class="w-[79%] ml-[21%] pt-5">
                <Home v-if="active === 1" @changetab="ID => {active = ID}"/>
                <Approve v-else-if="active === 2"/>
                <ProductApproval v-else-if="active === 3"/>
                <DeliverProduct v-else-if="active === 4"/>
                <ProductDelivery v-else-if="active === 5"/>
            </div>
        </div>
    </div>
</template>

<script>
    import Sidebar from './components/Sidebar.vue'
    import Header from './components/Header.vue'
    import ProfileBox from './components/ProfileBox.vue'
    import Login from './components/Login.vue'
    import Home from './components/Home.vue'
    import ProductApproval from './components/ProductApproval.vue'
    import ProductDelivery from './components/ProductDelivery.vue'
    import Approve from './components/Approve.vue'
import DeliverProduct from './components/DeliverProduct.vue'

    export default {
        data() {
            return {
                active: 1,
                loggedIn: true,
            }
        },
        components: {
    Sidebar,
    Header,
    ProfileBox,
    Login,
    Home,
    ProductApproval,
    ProductDelivery,
    Approve,
    DeliverProduct
},
        methods: {
            changeTab(tabID) {
                this.active = tabID
                window.scrollTo(0,0)
            }
        }
    }
</script>

<style>

</style>