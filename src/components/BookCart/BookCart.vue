<template>
    <template v-if="books.length > 0">
        <thead>
            <th></th>
            <th>书籍名称</th>
            <th>出版日期</th>
            <th>价格</th>
            <th>购买数量</th>
            <th>操作</th>
        </thead>
        <tbody>
            <tr v-for="(book, index) in books" :key="book.id">
                <td>{{ index + 1 }}</td>
                <td>{{ book.name }}</td>
                <td>{{ book.date }}</td>
                <td>￥{{ book.price }}</td>
                <td class="counter">
                    <button :disabled="book.count <= 1" @click="decreaseCount(index)">-</button>
                    {{ book.count }}
                    <button @click="increaseCount(index)">+</button>
                </td>
                <td>
                    <button @click="removeBook(index)">移除</button>
                </td>
            </tr>
        </tbody>
        <h2>总价: {{ totalPrice }}</h2>
    </template>
    <template v-else>当前购物车为空~</template>
</template>

<script lang="ts" setup>
import { computed, ref } from "vue"
const books = ref([
    {
        id: 1,
        name: "《算法导论》",
        date: "2006-9",
        price: 85.00,
        count: 1,
    },
    {
        id: 2,
        name: "《UNIX编程艺术》",
        date: "2006-2",
        price: 59.00,
        count: 1,
    },
    {
        id: 3,
        name: "编程珠玑",
        date: "2008-10",
        price: 39.00,
        count: 1,
    },
    {
        id: 4,
        name: "《代码大全》",
        date: "2006-3",
        price: 128.00,
        count: 1,
    },
])

const increaseCount = (index: number) => (books.value)[index].count += 1
const decreaseCount = (index: number) => (books.value)[index].count -= 1
const removeBook = (index: number) => (books.value).splice(index, 1)

const totalPrice = computed(() => {
    let finalPrice = 0
    for (const book of books.value) {
        finalPrice += book.count * book.price
    }
    return "￥" + finalPrice
})
</script>

<style scoped>
table {
    border: solid 1px #e9e9e9;
    border-collapse: collapse;
    border-spacing: 0;
}

th,
td {
    padding: 8px 16px;
    border: solid 1px #e9e9e9;
    text-align: left;
}

th {
    background-color: #f7f7f7;
    color: #5c6b77;
    font-weight: 600;
}

.counter {
    margin: 0 5px;
}
</style>