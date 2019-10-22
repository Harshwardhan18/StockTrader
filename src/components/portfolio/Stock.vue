<template>
    <div class="col-sm-6 col-md-5">
        <div class="panel panel-primary">
            <div class="panel-heading">
                 <h5 class="panel-title">
                    {{stock.name}}
                    <small>(Price : {{stock.price}} | Quantity: {{stock.quantity}})</small>    
                </h5>
            </div>
            <div class="panel-body">
                <div class="pull-left">
                    <input type="number" class="form-control" :class="{danger:inSufficientQuantity}" placeholder="quantity" v-model.number="quantity">
                </div>  
                <div class="pull-right">
                    <button class="btn btn-danger"
                    @click="sellStock"
                    :disabled = "inSufficientQuantity ||quantity <= 0 || !Number.isInteger(quantity)"
                    >{{inSufficientQuantity ? "Not Enough Shares" :'SELL'}}</button>  
                </div>  
            </div>
        </div>
    </div>
</template>
<script>
import {mapActions} from 'vuex';
export default {
    props : ['stock'],
    data(){
        return {
            quantity : 0
        };
    },
    computed: {
        inSufficientQuantity(){
            return this.quantity> this.stock.quantity;
        }
    },
    methods: {
        ...mapActions({
            placeSellOrder: 'sellStock'
        }),
        sellStock(){
            const order = {
                stockId: this.stock.id,
                stockPrice: this.stock.price,
                quantity: this.quantity
            };
            this.placeSellOrder(order);
            this.quantity = 0;
        }

    }
}
</script>
<style scoped>
    .danger{
        border: 1px solid red;
    }
</style>
    
