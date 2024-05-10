<template>
    <h3>History</h3>
    <ul class="list" id="list">
        <li v-for="t in transactions" :key="t.id" :class="t.amount<0 ?'minus' :'plus'">
            {{ t.text }}<span>Rs {{ t.amount }}</span>
            <button class="delete-btn">x</button>
        </li>
        <!-- <li class="minus">
            cash<span>-Rs 400</span>
            <button class="delete-btn">x</button>
        </li>
        <li class="plus">
            fiverr<span>Rs 800</span>
            <button class="delete-btn">x</button>
        </li> -->
    </ul>
</template>
<script>

export default{
    data(){
        return {
            transactions:[
                {id:1, text:'fiverr', amount:3000},
                {id:2, text:'camera', amount:-980},
                {id:3, text:'chegg', amount:500},
                {id:4, text:'biriyani', amount:-180}
            ]
        }
    }
}

</script>