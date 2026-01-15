<template>
  <div class="container">
    <h2>🍓 좋아하는 과일을 선택하세요</h2>

    <ul style="color: #c5a3ff" class="fruit-list">
      <li
        :style="{ color: '#c5a3ff', fontWeight: '700' }"
        v-for="(fruit, index) in fruits"
        :key="index"
        :class="{ selected: selectedFruit === fruit }"
        @click="selectFruit(fruit)"
      >
        {{ fruit }}
      </li>
    </ul>

    <p :style="{ color: '#c5a3ff', fontWeight: '700' }" v-if="selectedFruit" class="result">
      ✅ 당신이 선택한 과일은 <strong>{{ selectedFruit }}</strong> 입니다!
    </p>
  </div>
</template>

<script setup>
import { ref } from "vue"; // 'ref'를 불러와야 반응형 데이터를 만들 수 있어!

// 데이터 선언: ref() 함수로 감싸면 이 변수들이 '반응형'이 돼!
const fruits = ["사과", "바나나", "딸기", "포도", "수박"]; // 얘네는 변할 일 없으니까 굳이 ref 안 써도 돼!
const selectedFruit = ref(null); // 얘가 바뀔 수 있는 상태니까 ref로 감싸줘!

// 함수 선언: 평범한 JavaScript 함수처럼 쓰면 됨!
const selectFruit = (fruit) => {
  selectedFruit.value = fruit; // ref로 선언한 변수의 값에 접근할 땐 '.value'를 붙여야 해!
};
</script>

<style scoped>
/* style 태그는 Options API 방식과 동일 */
.container {
  font-family: Arial, sans-serif;
  text-align: center;
  padding: 20px;
}

h2 {
  color: #c5a3ff;
  margin-bottom: 20px;
}

.fruit-list {
  list-style: none;
  padding: 0;
  display: flex;
  justify-content: center;
  gap: 15px;
  margin-bottom: 30px;
}

.fruit-list li {
  padding: 10px 15px;
  border: 2px solid #c5a3ff;
  border-radius: 20px;
  cursor: pointer;
  transition: all 0.2s ease-in-out;
}

.fruit-list li:hover {
  background-color: #e0baff;
  color: #fff !important;
  border-color: #e0baff;
}

.fruit-list li.selected {
  background-color: #c5a3ff;
  color: #fff !important;
  border-color: #c5a3ff;
}

.result {
  margin-top: 30px;
  font-size: 1.2em;
}
</style>
