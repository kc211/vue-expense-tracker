<script>
import h from './components/h.vue'
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';
export default{
  components:{
    h,
    Balance,
    IncomeExpense,
    TransactionList,
    AddTransaction
  }
}
</script>


<template>
  
  <h/>
  <div class="container">
    <balance/>
    <IncomeExpense/>
    <TransactionList/>
    <AddTransaction/>
  </div>
</template>