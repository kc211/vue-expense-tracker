<template>
  <h3>History</h3>
  <ul class="list" id="list">
    <li
      v-for="t in transactions"
      :key="t.id"
      :class="t.amount < 0 ? 'minus' : 'plus'"
    >
      {{ t.text }}<span>Rs {{ t.amount }}</span>
      <button class="delete-btn" @click="deleteTransaction(t.id)">x</button>
    </li>
  </ul>
</template>
<script setup>
import { defineProps } from "vue";

const emit =defineEmits(['TransactionDeleted'])

const props = defineProps({
  transactions: {
    type: Array,
    required: true,
  },
});

const deleteTransaction = (id) => {
   emit('TransactionDeleted',id);
};
</script>