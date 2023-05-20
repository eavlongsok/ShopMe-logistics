<template>
    <PreviousDeliveryInfo v-if="infoPage" :delivery="delivery" @backToMain="infoPage = false"/>
    <div v-else>
        <h2 class="heading-2 mb-3">Product Delivery</h2>
        <div class="ml-4 mt-5 text-md">
            <span :class="{'bg-blue-700 text-white': minitab === 1}" class="border-2 border-gray-700 rounded-2xl border-opacity-75 cursor-pointer font-bold p-2" @click="minitab = 1; chosenCategory = 0; searched = false">Recent</span>
            <span :class="{'bg-blue-700 text-white': minitab === 2}" class="border-2 border-gray-700 rounded-2xl border-opacity-75 cursor-pointer font-bold p-2 ml-3" @click="minitab = 2; chosenCategory = 0">Search</span>
        </div>
        <div v-if="minitab === 1" class="mt-5 ml-3">
            <p class="capitalize text-xl font-bold text-gray-700">recently delivered products</p>

            <h2 class="text-xl text-center mt-16 font-bold" v-if="deliveries.length === 0">No product was found</h2>

            <Table class="w-11/12 mt-3 mb-5" :fields="fields" v-else-if="deliveries.length > 0">
                <tbody>
                    <tr v-for="(delivery, index) in deliveries" @mouseover="displayArrow('arrow', index+1)" @mouseleave="hideArrow('arrow', index+1)" @click="infoPage = true; chosenRow=index">
                        <td>{{ index + 1 }}</td>
                        <td>{{ delivery.purchase_info.id }}</td>
                        <td>{{ delivery.purchase_info.buyer_name }}</td>
                        <td>{{ delivery.purchase_info.address }}</td>
                        <td>{{ delivery.purchase_info.purchased_at }}</td>
                        <td>{{ delivery.purchase_info.eta }}</td>
                        <td>{{ delivery.purchase_info.delivered_at }}</td>
                        <td class="hover-on-arrow w-24" title="More details"><img src="forward-arrow.png" width="16" class="inline-block opacity-0" :ref="'arrow' + (index + 1)"/></td>
                    </tr>
                </tbody>
            </Table>
        </div>
        <div v-else-if="minitab === 2" class="mt-5 ml-3">
            <SearchBox action="/" @search="searched = true" class="inline-block"/>
            <small class="ml-3 text-sm block">Search for products by ID</small>

            <p class="ml-3 text-lg mt-5" v-if="searched">Search result for: "Some ID"</p>

            <h2 class="text-xl text-center mt-16 font-bold" v-if="searched && deliveries.length === 0">No product was found</h2>

            <Table class="w-11/12 mt-3 mb-5" :fields="fields" v-else-if="searched && deliveries.length > 0">
                <tbody>
                    <tr @mouseover="displayArrow('arrow', 0)" @mouseleave="hideArrow('arrow', 0)" @click="infoPage = true">
                        <td>1</td>
                        <td>{{ deliveries[0].purchase_info.id }}</td>
                        <td>{{ deliveries[0].purchase_info.buyer_name }}</td>
                        <td>{{ deliveries[0].purchase_info.address }}</td>
                        <td>{{ deliveries[0].purchase_info.purchased_at }}</td>
                        <td>{{ deliveries[0].purchase_info.eta }}</td>
                        <td>{{ deliveries[0].purchase_info.delivered_at }}</td>
                        <td class="hover-on-arrow w-24" title="More details"><img src="forward-arrow.png" width="16" class="inline-block opacity-0" ref="arrow0"/></td>
                    </tr>
                </tbody>
            </Table>
        </div>
    </div>
</template>

<script>
    import SearchBox from './SearchBox.vue';
    import Table from './Table.vue';
    import ApprovalInfo from './ApprovalInfo.vue';
    import PreviousDeliveryInfo from './PreviousDeliveryInfo.vue';
    export default {
        name: "ProductDelivery",
        data() {
            return {
                minitab: 1,
                searched: false,
                infoPage: false,
                chosenRow: 0,
                fields: ['No.', 'ID', 'Buyer Name', 'Address', 'Purchased At', 'ETA', 'Actual Date', ' '],
                deliveries: [
                    {
                        purchase_info: {
                            id: 101,
                            buyer_name: 'John Doe',
                            address: '123 Fake Street, Fake City, Fake Country',
                            purchased_at: '27/10/2020',
                            eta: '10/11/2020',
                            delivered_at: '9/11/2020',
                            delivered_by: 'Eav Long Sok (LG001)'
                        },
                        products: [
                            {
                                product_id: 1,
                                product_name: 'iPhone 12 Pro Max',
                                product_category: 'Phone',
                                product_category_id: 9,
                                product_price: 1200,
                                product_quantity: 1,
                            },
                            {
                                product_id: 2,
                                product_name: 'Asus ROG Strix G15',
                                product_category: 'PC',
                                product_category_id: 7,
                                product_price: 1200,
                                product_quantity: 1,
                            },
                            {
                                product_id: 3,
                                product_name: 'Canon EOS 5D Mark IV',
                                product_category: 'Camera',
                                product_category_id: 8,
                                product_price: 500,
                                product_quantity: 1,
                            }
                        ]
                    },
                    {
                        purchase_info: {
                            id: 102,
                            buyer_name: 'Jane Doe',
                            address: '456 Fake Street, Fake City, Fake Country',
                            purchased_at: '27/10/2020',
                            eta: '10/11/2020',
                            delivered_at: '9/11/2020',
                            delivered_by: 'Eav Long Sok (LG001)'
                        },
                        products: [
                            {
                                product_id: 4,
                                product_name: 'Some Chair',
                                product_category: 'Chair',
                                product_category_id: 5,
                                product_price: 100,
                                product_quantity: 5

                            },
                            {
                                product_id: 3,
                                product_name: 'Canon EOS 5D Mark IV',
                                product_category: 'Camera',
                                product_category_id: 8,
                                product_price: 500,
                                product_quantity: 1,
                            }
                        ]
                    }
                ],

                product: {
                    id: 1,
                    name: 'iPhone 12 Pro Max',
                    category: 'Phone',
                    price: 1200,
                    seller: 'ShopMe',
                    description: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Quisquam, voluptatum.',
                    delivered_at: '27/10/2020',
                    delivered_by: 'Eav Long Sok (LG001)',
                }
            }
        },
        components: {
            SearchBox, Table, ApprovalInfo, PreviousDeliveryInfo
        },
        methods: {
            displayArrow(ref, index) {
                if (index == 0) this.$refs[ref + index].classList.remove('opacity-0')
                else this.$refs[ref + index][0].classList.remove('opacity-0')
            },
            hideArrow(ref, index) {
                if (index == 0) this.$refs[ref + index][0].classList.add('opacity-0')
                else this.$refs[ref + index][0].classList.add('opacity-0')
            },
        },
        computed: {
            delivery() {
                return this.deliveries[this.chosenRow]
            }
        }
    }
</script>

<style scoped>

</style>