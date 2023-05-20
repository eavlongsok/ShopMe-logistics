<template>
    <div class="cursor-pointer" @click="$emit('backToMain')">
        <img src="back-arrow.png" width="16" class="inline-block">
        <span class="text-lg align-middle ml-2 underline hover:font-bold">Back</span>
    </div>

    <div class="text-lg ml-10 mt-4">
        <p>Purchase ID: {{ delivery.purchase_info.id }}</p>
        <p>Buyer Name: {{ delivery.purchase_info.buyer_name }}</p>
        <p>Address: {{ delivery.purchase_info.address }}</p>
        <p>Purchased At: {{ delivery.purchase_info.purchased_at }}</p>
        <p>Estimated Time of Arrival: {{ delivery.purchase_info.eta }}</p>
    </div>

    <Table :fields="fields" class="w-11/12 mt-5 mb-5">
        <caption class="mb-2 font-bold text-xl">Purchased Products</caption>
        <tbody>
            <tr v-for="product in delivery.products">
                <td>{{ product.product_id }}</td>
                <td>{{ product.product_name }}</td>
                <td>{{ product.product_category }}</td>
                <td>{{ product.product_price }}</td>
                <td>{{ product.product_quantity }}</td>
            </tr>
        </tbody>
    </Table>

    <button class="block bg-blue-600 rounded-xl text-xl p-2 border-2 border-black hover:bg-blue-700 font-bold text-white mt-5 w-72 select-none ml-3" @click="$event => {
        $event.target.innerText = 'Button Clicked!'
    }">I Will Deliver the Product</button>

</template>

<script>
    import Table from './Table.vue';

    export default {
        name: "ApprovalInfo",
        data() {
            return {
                fields: ['ID', 'Name', 'Category', 'Price', 'Quantity']
            }
        },
        props: ["delivery"],
        emits: ["backToMain"],
        components: { Table }
    }
</script>

<style scoped>

</style>