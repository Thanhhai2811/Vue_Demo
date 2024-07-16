<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import VueRouter from './components/VueDay.vue'
import { ref, watch, computed } from 'vue'

const firtName = ref('Name')
const lastName = ref('Gender')
const gender = ref(1)  // 1: name 2: nữ
const amount = ref(100000)
const msg = ref('Hello Vue')
const products = ref([
    { id: 1, name: 'iphone12', qty: 2, price: 100 },
    { id: 2, name: 'iphone13', qty: 5, price: 200 },
    { id: 4, name: 'iphone14', qty: 9, price: 400 },
])

// VD về Props
const labelUploadImage = ref({
    User: 'chọn ảnh cho user',
    product: 'chọn ảnh cho sản phẩm'
})

// VD về Emits
const UploadImage = (value: object) => {
    console.log('Save image user',)
}

// VD về watch
watch(products, (products) => {
    totalAmount(products)
}, {deep: true} )

watch(msg, (newValue) => {
    console.log(newValue)
})

// VD về computed
const fullname = computed({
    get: () => {
        return firtName.value + lastName.value
    },
    set: (firtNameValue, lastNameValue) => {
    },
})

const commissions = computed(() => {
    if (gender.value === 1 && amount.value > 100000 && amount.value < 1000000) {
        return '15%'
    }

    if (gender.value === 2 && amount.value > 100000 && amount.value < 5000000) {
        return '15%'
    }

    if (gender.value === 1) {
        return '10%'
    }

    if (gender.value === 2) {
        return '12%'
    }
})

const totalAmount = (products: array) => {
    let total = 0
    products.forEach((product: object) => {
        total += product.price * product.qty
    })

    amount.value = total
}

totalAmount(products.value)

</script>

<template>
    <div>
        <h3>Create user</h3>
        <VueRouter @choose-file="UploadImage" :labelName="labelUploadImage.User"></VueRouter>
    </div>

    <div>
        <h3>Create product</h3>
        <VueRouter :labelName="labelUploadImage.product"></VueRouter>
        <p>commissions: {{ commissions }}</p>
        <button @click="msg = 100">Change Message</button>
        {{ msg }}
    </div>
    <table border="1" width="500">
        <tr>
            <td>ID</td>
            <td>Name</td>
            <td>Qty</td>
            <td>Price</td>
        </tr>

        <tr :key="index" v-for="(product, index) in products">
            <td>{{product.id}}</td>
            <td>{{product.name}}</td>
            <td> <input v-model="product.qty" /></td>
            <td>{{product.price}}</td>
            <td>{{product.price * product.qty}}</td>
        </tr>
        <p>Tổng tiền: {{ amount }}</p>
    </table>
    <!--  -->

    <div>
        {{ fullname }}
    </div>
</template>