<template>
    <div v-if="productList.length > 0">
      <h3 class="text-center">List of Added Products</h3>
      <div class="row product-container">
        <product :key="product" v-for="product in productList">
          <div class="card-img">
            <img class="card-img-top" width="130px" height="130px" :src="product.selectedImage" alt="Card image cap">
          </div>
          <div class="card-body">
            <h5 class="card-title">{{ product.name }}</h5>
            <small>
              <strong>Count : </strong> {{ product.count }}
            </small>
            <br>
            <small>
              <strong>Price : </strong> {{ product.price }}$
            </small>
            <br>
            <small>
              <strong>Sum : </strong> {{ product.totalPrice }}$
            </small>
          </div>
        </product>
      </div>
    </div>
</template>

<script>
import Product from './Product'
import { eventBus } from '../main'

export default {
    components: {
        product: Product
    },
    data() {
        return {
            productList: []
        }
    },
    created() {
        eventBus.$on("productAdded", (product) => {
            if (this.productList.length < 10) {
                this.productList.push(product);
                eventBus.$emit("productListUpdated", this.productList.length)
            }else{
                alert("You cannot add more product!")
            }
        })
    },
}
</script>

<style scoped>
.card-img{
    height: 145px;
    line-height: 145px;
}
.card-body{
    min-height: 145px;
}
</style>
