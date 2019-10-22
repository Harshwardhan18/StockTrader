<template>
    <div>
        <div v-if="stocks.length > 0">
            <app-stock v-for="stock in stocks" :stock='stock'></app-stock>
        </div>
        <div v-else class="alert alert-warning center" role="alert">No stocks for trading!!!</div>    
    </div>
</template>

<script>
import {mapGetters} from 'vuex';
import Stock from './Stock.vue';

export default {
    computed : {
        ...mapGetters({
            stocks: 'stockPortfolio'
        })
    },
    components: {
        appStock: Stock
    }
}
</script>
<style scoped>
    .center {
        text-align: center;
    }
</style>
    
