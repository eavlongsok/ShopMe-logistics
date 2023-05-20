<template>
    <div class="cursor-pointer" @click="$emit('backToMain')">
        <img src="back-arrow.png" width="16" class="inline-block">
        <span class="text-lg align-middle ml-2 underline hover:font-bold">Back</span>
    </div>
    <div class="grid grid-cols-5 gap-6 mx-auto mt-5 w-5/6 select-text pb-10">
        <div class="w-full col-span-2">
            <img src="iphone12.jpg" class="w-full"/>
            <button class="block bg-green-600 rounded-xl text-xl p-2 border-2 border-black hover:bg-green-700 font-bold text-white mt-5 w-32 ml-auto select-none" @click="$emit('approve')">{{product.approved ? 'Approved!' : 'Approve'}}</button>
        </div>
        <div class="col-span-3">
            <div class="my-row">
                <div class="col-one">
                    ID:
                </div>
                <div class="col-two">
                    {{ product.id }}
                </div>
            </div>

            <div class="my-row">
                <div class="col-one">
                    Product Name:
                </div>
                <div class="col-two">
                    {{ product.name }}
                </div>
            </div>

            <div class="my-row">
                <div class="col-one">
                    Category:
                </div>
                <div class="col-two">
                    {{ product.category }}
                </div>
            </div>

            <div class="my-row">
                <div class="col-one">
                    Seller:
                </div>
                <div class="col-two">
                    {{ product.seller }}
                </div>
            </div>

            <div class="my-row">
                <div class="col-one">
                    Eamil:
                </div>
                <div class="col-two">
                    {{ product.seller_email }}
                </div>
            </div>

            <div class="my-row">
                <div class="col-one">
                    Quantity:
                </div>
                <div class="col-two">
                    {{ product.quantity }}
                </div>
            </div>


            <div class="my-row">
                <div class="col-one">
                    Description:
                </div>
                <div class="col-two">
                    {{ product.description }}
                </div>
            </div>

            <div class="my-row">
                <div class="col-one">
                    Submission Date:
                </div>
                <div class="col-two">
                    {{ product.submission_date }}
                </div>
            </div>

        </div>
    </div>
</template>

<script>
    export default {
        name: 'ApprovalInfo',
        props: ['product'],
        emits: ['backToMain', 'approve']
    }
</script>

<style scoped>
    .col-one {
        @apply text-gray-800 font-bold capitalize justify-self-end;
    }

    .col-two {
        @apply col-span-2;
    }

    .my-row {
        @apply grid grid-cols-3 gap-8 justify-between text-xl my-2;
    }
</style>