<script setup>
import { ref } from 'vue';

const deposit = ref(10250000);

const A = 300000;
const B = 0.00000006;
const C = 110000;
const baseDeposit = 10250000;

const calculateRent = (depositValue) => {
  const rent = A * Math.exp(-B * (depositValue - baseDeposit)) + C;
  return Math.round(rent);
};
</script>

<template>
  <div class="max-w-md mx-auto p-6 space-y-8">
    <h2 class="text-2xl font-bold">보증금 계산기</h2>

    <div class="space-y-4">
      <label for="deposit" class="block text-lg font-medium">보증금 (₩)</label>
      <input
        id="deposit"
        type="number"
        v-model="deposit"
        :min="10250000"
        :max="67000000"
        step="100000"
        class="w-full p-3 border rounded-lg text-lg"
      />
    </div>

    <div class="text-xl font-medium">
      예상 월세: <span class="text-green-600 font-bold">₩{{ calculateRent(deposit).toLocaleString() }}</span>
    </div>
  </div>
</template>

<style scoped>
/* 스타일 수정 */
.max-w-md {
  max-width: 400px; /* 카드 크기 */
}

h2 {
  font-size: 2rem; /* 제목 글자 크기 */
}

label {
  font-size: 1.25rem; /* 라벨 글자 크기 */
}

input {
  font-size: 1.25rem; /* 입력 필드 글자 크기 */
}

.text-xl {
  font-size: 1.5rem; /* 예상 월세 텍스트 크기 */
}

.text-green-600 {
  font-size: 1.75rem; /* 월세 금액 텍스트 크기 */
}
</style>