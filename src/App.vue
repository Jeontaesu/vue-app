<template>
  <div class="container">
    <h2>🍓 좋아하는 과일을 선택하세요</h2>

    <ul class="fruit-list">
      <li v-for="(fruit, index) in fruits" :key="index" :class="{ selected: selectedFruit === fruit }" @click="selectFruit(fruit)">
        {{ fruit }}
      </li>
    </ul>

    <p v-if="selectedFruit" class="result">
      ✅ 당신이 선택한 과일은 <strong>{{ selectedFruit }}</strong> 입니다!
    </p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const fruits = ref(["사과", "바나나", "포도", "복숭아", "딸기"]);
const selectedFruit = ref("");

function selectFruit(fruit) {
  selectedFruit.value = fruit;
}
</script>

<style scoped>
.container {
  max-width: 400px;
  margin: 40px auto;
  padding: 24px;
  background: #fff;
  border-radius: 12px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.06);
  font-family: "Segoe UI", sans-serif;
}

h2 {
  text-align: center;
  margin-bottom: 16px;
}

.fruit-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.fruit-list li {
  background: #f1f1f1;
  padding: 10px 14px;
  margin-bottom: 10px;
  border-radius: 8px;
  cursor: pointer;
  transition: 0.3s;
  font-size: 16px;
  text-align: center;
}

.fruit-list li:hover {
  background: #e3e3e3;
}

.fruit-list li.selected {
  background-color: #42b983;
  color: #fff;
  font-weight: bold;
  transform: scale(1.02);
}

.result {
  text-align: center;
  margin-top: 20px;
  font-size: 16px;
  color: #999;
}
</style>
