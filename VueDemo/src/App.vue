<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import VueRouter from './components/VueDay.vue'
import {ref, watch, computed} from 'vue'

const firtlabelName = ref('Name')
const firtlabelGender = ref('Gender')
const gender = ref(1)  // 1: name 2: nữ
const amount = ref(100000)

// VD về Props
const labelUploadImage = ref({
    User : 'chọn ảnh cho user',
    product : 'chọn ảnh cho sản phẩm'
})

// VD về Emits
const UploadImage = (value: object) => {
    console.log('Save image user',)
}

// VD về computed
const fullname = computed(() => {
    return firtlabelName.value + firtlabelGender.value
})

const commissions = computed(() => {
    if(gender.value === 1 && amount.value > 100000 &&  amount.value < 1000000) {
        return '15%'
    }

    if(gender.value === 2 && amount.value > 100000 &&  amount.value < 5000000) {
        return '15%'
    }

    if(gender.value === 1) {
        return '10%'
    }

    if(gender.value === 2) {
        return '12%'
    }
})

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
    </div>

    <!--  -->

    <div>
        {{ fullname}}
    </div>
</template>

