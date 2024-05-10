<template>
  <h/>
  <div class="container">
    <balance :total="total"/>
    <IncomeExpense/>
    <TransactionList :transactions="transactions"/>
    <AddTransaction/>
  </div>
</template>

<script setup>
import h from './components/h.vue'
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';
import {computed, ref} from'vue'

const transactions=ref([
                {id:1, text:'fiverr', amount:3000},
                {id:2, text:'camera', amount:-980.89},
                {id:3, text:'chegg', amount:500},
                {id:4, text:'biriyani', amount:-180}
            ]);

const total = computed( ()=>{
  return transactions.value.reduce((acc,transaction)=>{
    return acc+transaction.amount
  },0);
})
</script>