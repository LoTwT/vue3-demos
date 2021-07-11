<template>
  <h1>demos list</h1>
  <div>
    <button @click="isBookCartShow = !isBookCartShow">showBookCart</button>
    <BookCart v-if="isBookCartShow" />
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import BookCart from "@/components/BookCart.vue"

const isBookCartShow = ref(false)
</script>

