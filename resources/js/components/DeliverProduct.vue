<template>
    <DeliveryInfo v-if="infoPage" :delivery="delivery" @backToMain="infoPage = false"/>
    <div v-else>
        <h2 class="heading-2 mb-3">Deliver Products</h2>
        <SearchBox action="/" @search="searched = true" class="inline-block"/>
        <small class="ml-3 text-sm block">Search for products by ID</small>

        <Table :fields="fields" class="w-11/12 mt-3 mb-5" v-if="searched">
            <tbody>
                <tr @mouseover="displayArrow()" @mouseleave="hideArrow()" @click="infoPage = true">
                    <td>{{ delivery.purchase_info.id }}</td>
                    <td>{{ delivery.purchase_info.buyer_name }}</td>
                    <td>{{ delivery.purchase_info.address }}</td>
                    <td>{{ delivery.purchase_info.purchased_at }}</td>
                    <td>{{ delivery.purchase_info.eta }}</td>
                    <td class="hover-on-arrow w-24" title="More details"><img src="forward-arrow.png" width="16" class="inline-block opacity-0" ref="arrow"/></td>
                </tr>
            </tbody>
        </Table>
    </div>
</template>

<script>
    import DeliveryInfo from './DeliveryInfo.vue';
    import SearchBox from './SearchBox.vue';
    import Table from './Table.vue';

    export default {
        name: 'Approve',
        data() {
            return {
                infoPage: false,
                fields: ['ID', 'Buyer Name', 'Address', 'Purchased At', 'ETA', ' '],
                searched: false,
                delivery: {
                    purchase_info: {
                        id: 101,
                        buyer_name: 'John Doe',
                        address: '123 Fake Street, Fake City, Fake Country',
                        purchased_at: '27/10/2020',
                        eta: '10/11/2020',
                    },
                    products: [{
                        product_id: 1,
                        product_name: 'iPhone 12 Pro Max',
                        product_category: 'Phone',
                        product_category_id: 9,
                        product_price: 1200,
                        product_quantity: 1,
                    }, {
                        product_id: 2,
                        product_name: 'Asus ROG Strix G15',
                        product_category: 'PC',
                        product_category_id: 7,
                        product_price: 1200,
                        product_quantity: 1,
                    }, {
                        product_id: 3,
                        product_name: 'Canon EOS 5D Mark IV',
                        product_category: 'Camera',
                        product_category_id: 8,
                        product_price: 500,
                        product_quantity: 1,
                    }
                ]
                }

            }
        },
        components: { SearchBox, Table, DeliveryInfo },
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