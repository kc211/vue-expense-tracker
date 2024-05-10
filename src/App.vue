<template>
  <h/>
  <div class="container">
    <balance :total="+total"/>
    <IncomeExpense :income="+income" :expense="+expense"/>
    <TransactionList :transactions="transactions" @TransactionDeleted="handleTransactionDelete"/>
    <AddTransaction @transactionSubmitted="handleTransactionSubmitted"/>
  </div>
</template>

<script setup>
import h from './components/h.vue'
import Balance from './components/Balance.vue';
import IncomeExpense from './components/IncomeExpense.vue';
import TransactionList from './components/TransactionList.vue';
import AddTransaction from './components/AddTransaction.vue';
import {computed, ref} from'vue'
import {useToast} from 'vue-toastification';
const transactions=ref([
                // {id:1, text:'fiverr', amount:3000},
                // {id:2, text:'camera', amount:-980.89},
                // {id:3, text:'chegg', amount:500},
                // {id:4, text:'biriyani', amount:-180}
            ]);



const savedTransactions = JSON.parse(localStorage.getItem('transactions'))

if(savedTransactions)
{
  transactions.value=savedTransactions;
}
const toast = useToast();

//get total
const total = computed( ()=>{
  return transactions.value.reduce((acc,transaction)=>{
    return acc+transaction.amount
  },0);
})

//get income

const income=computed(()=>{
  return transactions.value
  .filter((transaction)=>transaction.amount>0)
  .reduce((acc,transaction)=>{
    return acc+transaction.amount;
  },0).toFixed(2)
})

//get expense

const expense=computed(()=>{
  return transactions.value.filter((transaction)=>transaction.amount<0)
  .reduce((acc,transaction)=>{
    return acc+transaction.amount;
  },0).toFixed(2);
})


//new transaction

const handleTransactionSubmitted =(transactionData)=>{
  console.log(transactionData);
  transactions.value.push({
    id:generateUniqueId(),
    text:transactionData.text,
    amount:transactionData.amount
  });

  saveToLocalStorage();
  console.log(generateUniqueId());
  toast.success('Transaction Added')
}


const generateUniqueId=()=>{
  return Math.floor(Math.random()*100000)
}



//delete a transaction

const handleTransactionDelete=(id)=>{
  console.log(id);
  transactions.value= transactions.value.filter((transaction)=>
transaction.id!==id);

saveToLocalStorage();
toast.success('Transaction Deleted')
  
};


// save to local storage

const saveToLocalStorage = ()=>{
  localStorage.setItem('transactions',JSON.stringify(transactions.value));
}
</script>