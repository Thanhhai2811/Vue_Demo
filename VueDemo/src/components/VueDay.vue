<template>
  <div>
      <h3>{{ labelName }}</h3>
      <input type="file" name="file" @change="chooseFile"/>
      <br/>
  </div>
</template>

<script setup lang="ts">
import {defineProps, defineEmits} from 'vue'

const props = defineProps ({
  labelName : {
    type : String,
    default: 'Chọn file'
  }
})

const emits = defineEmits(['choose-file']) // (choose-file) là giá trị được truyền 


const chooseFile = (event: any) => {
  // gửi thông tin đến component cha 
  
  let fileInfo = event.target.files[0]
  emits('choose-file', fileInfo)
}
</script>

<style>

</style>