<template>
    <div class="tab-control">
        <div
            class="tab-control-item"
            :class="{ active: currentIndex === index }"
            v-for="(title, index) in titles"
            :key="index"
            @click="changeCurrentIndex(index)"
        >
            <span>{{ title }}</span>
        </div>
    </div>
</template>

<script lang="ts" setup>
import { ref } from "vue"

defineProps({
    titles: {
        type: Array,
        required: true
    }
})

const emit = defineEmits(["titleClick"])

const currentIndex = ref(0)

const changeCurrentIndex = (index: number) => {
    currentIndex.value = index
    emit("titleClick", currentIndex.value)
}
</script>

<style scoped>
.tab-control {
    display: flex;
    margin-bottom: 10px;
}

.tab-control-item {
    flex: 1;
    text-align: center;
}

.tab-control-item.active {
    color: red;
}

.tab-control-item.active span {
    border-bottom: solid 3px red;
    padding: 3px 5px;
}
</style>