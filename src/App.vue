<template>
  <h1>demos list</h1>
  <button @click="isBookCartShow = !isBookCartShow">showBookCart</button>
  <button @click="isTabControlShow = !isTabControlShow">ShowTabControl</button>
  <book-cart v-if="isBookCartShow" />
  <div v-if="isTabControlShow" class="tab-control-wrapper">
    <tab-control :titles="tabControlTitles" @titleClick="titleClick" />
    <div>{{ tabControlContents[currentIndex] }}</div>
  </div>
</template>

<script lang="ts" setup>
import { ref } from "vue";
import BookCart from "@/components/BookCart/BookCart.vue"
import TabControl from "@/components/TabControl/TabControl.vue"

const isBookCartShow = ref(false)

// TabControl
const isTabControlShow = ref(false)
const tabControlTitles = ["鞋子", "衣服", "裤子"]
const tabControlContents = ["鞋子页面", "衣服页面", "裤子页面"]
const currentIndex = ref(0)
const titleClick = (index: number) => currentIndex.value = index
</script>

<style scoped>
.tab-control-wrapper {
  width: 300px;
  height: 300px;
  border: solid 1px #000;
}
</style>
