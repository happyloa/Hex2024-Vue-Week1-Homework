<script setup>
import { ref } from "vue"; // 引入 Vue 的 ref 函數，讓資料變為響應式

// 引入初始的品項資料，並將其命名為 initialItems
import { items as initialItems } from "./data/items";

// 將初始的品項資料設定為響應式的 items，這樣 Vue 可以在資料變化時自動更新 UI
const items = ref(initialItems);

// 用於存儲當前正在編輯的品項的名稱
const tempName = ref("");

// 用於存儲當前正在編輯的品項 ID
const editingItemId = ref(null);

// 編輯品項名稱
const editItemName = {
  on(item) {
    // 當雙擊品項名稱時，進入編輯模式
    editingItemId.value = item.id;
    tempName.value = item.name;
  },
  save(item) {
    // 保存編輯後的名稱，並退出編輯模式
    item.name = tempName.value;
    editingItemId.value = null;
  },
  cancel() {
    // 取消編輯，恢復原來的名稱
    editingItemId.value = null;
  },
};

// 定義一個函數 changeStockQty，用來改變品項的庫存數量
// item: 代表要操作的品項
// action: 代表操作的類型，'plus' 增加庫存，'minus' 減少庫存
const changeStockQty = (item, action) => {
  if (action === "plus") {
    // 如果操作類型是 'plus'，則增加該品項的庫存
    item.stock += 1;
  } else if (action === "minus") {
    // 如果操作類型是 'minus'，且當前庫存大於或等於 1，則減少庫存
    if (item.stock >= 1) item.stock -= 1;
  }
};
</script>

<template>
  <h1>六角學院 2024 Vue 前端新手營</h1>
  <!-- 主標題 -->
  <p>第一週作業 by Aaron</p>
  <!-- 副標題，作者標記 -->
  <hr />
  <table>
    <thead>
      <tr>
        <th scope="col">品項</th>
        <!-- 表格頭部，表示品項名稱 -->
        <th scope="col">描述</th>
        <!-- 表格頭部，表示品項描述 -->
        <th scope="col">價格</th>
        <!-- 表格頭部，表示品項價格 -->
        <th scope="col">庫存</th>
        <!-- 表格頭部，表示品項庫存 -->
      </tr>
    </thead>
    <tbody>
      <!-- 使用 v-for 指令遍歷 items 數組，為每個品項生成一行 -->
      <tr v-for="item in items" :key="item.id">
        <td>
          <template v-if="editingItemId === item.id">
            <!-- 當前品項處於編輯模式時，顯示輸入框和控制按鈕 -->
            <input v-model="tempName" type="text" />
            <button class="btn" @click="editItemName.save(item)">儲存</button>
            <button class="btn" @click="editItemName.cancel()">取消</button>
          </template>
          <template v-else>
            <!-- 非編輯模式下顯示名稱，並監聽雙擊事件 -->
            <span @dblclick="editItemName.on(item)">{{ item.name }}</span>
          </template>
        </td>
        <td>
          <small>{{ item.description }}</small>
          <!-- 顯示品項描述 -->
        </td>
        <td>{{ item.price }}</td>
        <!-- 顯示品項價格 -->
        <td>
          <!-- 庫存控制區域，減少庫存的按鈕 -->
          <button
            class="btn"
            type="button"
            @click="changeStockQty(item, 'minus')">
            <!-- 點擊觸發減少庫存 -->
            -
          </button>
          <div class="stock">
            {{ item.stock }}
            <!-- 顯示品項當前的庫存 -->
          </div>
          <!-- 增加庫存的按鈕 -->
          <button
            class="btn"
            type="button"
            @click="changeStockQty(item, 'plus')">
            <!-- 點擊觸發增加庫存 -->
            +
          </button>
        </td>
      </tr>
    </tbody>
  </table>
  <hr />
  <p>💡對品項名稱點兩下即可編輯</p>
</template>

<style scoped>
@import "./assets/AppStyle.css";
</style>
