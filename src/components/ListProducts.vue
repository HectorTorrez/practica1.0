<template>
    <div id="container">
        <a href="#" class="btn btn-primary" data-bs-toggle="modal" data-bs-target="#exampleModal">Add cart</a>
        <div class="row">
  <div class="col-sm-6 " v-for="(item, index) in items" v-bind:key="index">
    <div class="card">
      <div class="card-body">
        <h5 class="card-title">{{item.productName}}</h5>
        <p class="card-text">{{item.description}}</p>
        <input type="number" v-model="item.quantity" id="">
        <a href="#" class="btn btn-primary" @click="add(index)">Add cart</a>
      </div>
    </div>
  </div>
  
</div>

<cart-items :cartProducts="cartProducts"/>
    </div>
</template>

<script>

import products from '../data/products.json'
import CartItems from './CartItems.vue'

export default {
    name:'ListProducts',
    components:{
        CartItems
    },
    data(){
        return{
            items:products,
            cartProducts:[]
        }
    },
    methods:{
        add:function(index){
            this.cartProducts.push(
                {
                    productName: this.items[index].productsName,
                    description: this.items[index].description,
                    quantity: this.items[index].quantity,
                    price: this.items[index].price
                }
            )
        }
    }
}
</script>