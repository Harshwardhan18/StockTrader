<template>
    <div>
        <app-stock v-for="stock in stocks" :stock="stock"></app-stock>
    </div>
</template>
<script>
import Stock from './Stock.vue';
export default {
    data(){
        return {
            stocks :[
                {id: 1,name: 'Apple',price: 180},
                {id: 2,name: 'Google',price: 150},
                {id: 3,name: 'Samsung',price: 230},
                {id: 4,name: 'Sony',price: 18},
            ]
        };
    },
    components : {
        appStock : Stock
    }
}
</script>
    
