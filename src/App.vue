<script setup>
import { ref } from "vue";

import { items as initialItems } from "./data/items";
const items = ref(initialItems);

const changeStockQty = (item, action) => {
  if (action === "plus") {
    item.stock += 1;
  } else if (action === "minus") {
    if (item.stock >= 1) item.stock -= 1;
  }
};
</script>

<template>
  <h1>六角學院 2024 Vue 前端新手營</h1>
  <p>第一週作業 by Aaron</p>
  <hr />
  <table>
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col">價格</th>
        <th scope="col">庫存</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="item in items" :key="item.id">
        <td>
          {{ item.name }}
        </td>
        <td>
          <small>{{ item.description }}</small>
        </td>
        <td>{{ item.price }}</td>
        <td>
          <button
            class="btn"
            type="button"
            @click="changeStockQty(item, 'minus')">
            -
          </button>
          <div class="stock">
            {{ item.stock }}
          </div>
          <button
            class="btn"
            type="button"
            @click="changeStockQty(item, 'plus')">
            +
          </button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
@import "./assets/AppStyle.css";
</style>
