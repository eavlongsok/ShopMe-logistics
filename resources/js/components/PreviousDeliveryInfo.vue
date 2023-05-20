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
        <p>Estimated Time of Arrvival: {{ delivery.purchase_info.eta }}</p>
        <p>Actual Time of Arrival: {{ delivery.purchase_info.delivered_at }}</p>
        <p>Delivered By: {{ delivery.purchase_info.delivered_by }}</p>
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