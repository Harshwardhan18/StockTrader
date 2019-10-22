<template>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
        <router-link to="/" class="navbar-brand">
            Stock Trader
        </router-link>
        <div class="collapse navbar-collapse">
            <ul class="navbar-nav nav">
                <router-link to="/portfolio" active-class="active" tag="li"><a>Portfolio</a></router-link>
                <router-link to="/stocks" active-class="active" tag="li"><a>Stocks</a></router-link>
            </ul>
            <strong class="navbar-text navbar-right">Funds: {{funds | currency}}</strong>
            <ul class="nav navbar-nav navbar-right">
                <li><a @click="endDay" href="#">End Day</a></li>
                <li class="dropdown" :class="{open:isDropdownOpen}" @click="isDropdownOpen = !isDropdownOpen">
                    <a class="dropdown-toggle" href="#" id="navbarDropdown" role="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="false">
                    Save & Load
                    <span class="caret"></span>
                    </a>                    
                    <ul class="dropdown-menu" aria-labelledby="navbarDropdown">
                        <li><a class="dropdown-item" href="#" @click="saveData">Save Data</a></li>
                        <li><a class="dropdown-item" href="#" @click="loadData">Load Data</a></li>
                    </ul>
                </li>
            </ul>           
        </div>
    </nav>
</template>

<script>
import {mapActions} from 'vuex';
export default {
    data(){
        return {
            isDropdownOpen: false
        };
    },
    computed: {
        funds(){
            return this.$store.getters.funds;
        }
    },
    methods: {
        ...mapActions({
            randomizeStocks: 'randomizeStocks',
            fetchData :'loadData'
        }),
        endDay(){
            this.randomizeStocks();
        },
        saveData(){
            const data = {
                funds: this.$store.getters.funds,
                stocks: this.$store.getters.stocks,
                stockPortfolio: this.$store.getters.stockPortfolio
            };
            this.$http.put('data.json',data);
        },
        loadData(){
            this.fetchData();
        }
    }
}
</script>

<style scoped>
    strong{
        color:rgba(48, 92, 187, 0.699)
    }
</style>


    
