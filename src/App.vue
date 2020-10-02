<template>
  <div class="container">
    <h1 class="text-center">Product Add App</h1>
    <hr>
    <new-product></new-product>
    <br><br>
    <progressbar></progressbar>
    <br><br>
    <product-list></product-list>
  </div>
</template>

<script>
import NewProduct from './components/NewProduct'
import ProductList from './components/ProductList'
import Progressbar from './components/Progressbar'

export default {
  components: {
    newProduct : NewProduct,
    productList : ProductList,
    progressbar : Progressbar
  }
}
</script>

<style>
  body {
    background-color: aliceblue;
    padding-top: 20px;
    padding-bottom: 20px;
  }

  .card{
    margin-right: 5px;
    margin-bottom: 5px;
  }

  .card-img{
    height: 145px;
    line-height: 145px;
  }
  .card-body{
    min-height: 145px;
    margin: auto;
  }

  .card:last-child{
    margin-right: 0px;
  }

  .col-md-2{
    max-width: 15.666667%!important;
  }

  .product-container{
    margin-left: 15px;
  }

</style>

