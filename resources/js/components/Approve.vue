<template>
    <ProductInfo v-if="infoPage" :product="product" @backToMain="infoPage = false" @approve="product.approved = true"/>
    <div v-else>
        <h2 class="heading-2 mb-3">Approve Products</h2>
        <SearchBox action="/" @search="searched = true" class="inline-block"/>
        <small class="ml-3 text-sm block">Search for products by ID</small>

        <Table :fields="fields" class="w-11/12 mt-3 mb-5" v-if="searched">
            <tbody>
                <tr @mouseover="displayArrow()" @mouseleave="hideArrow()" @click="infoPage = true">
                    <td>{{ product.id }}</td>
                    <td>{{ product.name }}</td>
                    <td>{{ product.category }}</td>
                    <td>{{ product.seller }}</td>
                    <td>{{ product.quantity }}</td>
                    <td class="hover-on-arrow w-24" title="More details"><img src="forward-arrow.png" width="16" class="inline-block opacity-0" ref="arrow"/></td>
                </tr>
            </tbody>
        </Table>
    </div>
</template>

<script>
    import ProductInfo from './ProductInfo.vue';
    import SearchBox from './SearchBox.vue';
    import Table from './Table.vue';

    export default {
        name: 'Approve',
        data() {
            return {
                infoPage: false,
                fields: ['ID', 'Product Name', 'Category', 'Store Name', 'Quantity', ' '],
                searched: false,
                product: {
                    id: 1,
                    name: 'iPhone 12 Pro Max',
                    category: 'Phone',
                    category_id: 9,
                    seller: 'ShopMe',
                    seller_email: 'esok@paragoniu.edu.kh',
                    quantity: 50,
                    description: 'The iPhone 12 Pro Max is Apple\'s biggest and best phone they\'ve ever created, embodying everything they\'ve learned over the last 13 years of making iPhones.',
                    submission_date: '27/10/2020',
                    approved: false
                }
            }
        },
        components: { SearchBox, Table, ProductInfo },
        methods: {
            displayArrow() {
                this.$refs.arrow.classList.remove('opacity-0')
            },
            hideArrow() {
                this.$refs.arrow.classList.add('opacity-0')
            }
        }
    }
</script>

<style scoped>

</style>