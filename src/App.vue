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
      <!-- 여기도 똑같이! -->
      ✅ 당신이 선택한 과일은 <strong>{{ selectedFruit }}</strong> 입니다!
    </p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      fruits: ["사과", "바나나", "딸기", "포도", "수박"],
      selectedFruit: null,
    };
  },
  methods: {
    selectFruit(fruit) {
      this.selectedFruit = fruit;
    },
  },
};
</script>

<style scoped>
/* style 태그도 추가해줬어! container랑 selected도 한번 넣어봐봐 */
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
  color: #fff !important; /* 호버 시 글자색 변경 */
  border-color: #e0baff;
}

.fruit-list li.selected {
  background-color: #c5a3ff;
  color: #fff !important; /* 선택 시 글자색 변경 */
  border-color: #c5a3ff;
}

.result {
  margin-top: 30px;
  font-size: 1.2em;
}
</style>
