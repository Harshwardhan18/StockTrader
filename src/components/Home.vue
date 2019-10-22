<template>
    <div class="card">
        <div class="card-body">
            <h1 class="card-title">Trade or View your portfolio</h1>
            <h6 class="card-text">You may save or load your data</h6>
            <h6 class="card-text">Click on End day to begin a new day</h6>
            <hr>
            <p class="card-text">Your Funds: {{funds | currency}}</p>
        </div>
        
    </div>
</template>

<script>
export default {
    computed: {
        funds(){
            return this.$store.getters.funds;
        }
    }
}
</script>
    
