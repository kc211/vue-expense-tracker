<script>
import h from './components/h.vue'
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
export default{
  components:{
    h,
    Balance,
    IncomeExpense
  }
}
</script>


<template>
  
  <h/>
  <div class="container">
    <balance/>
    <IncomeExpense/>
  </div>
</template>