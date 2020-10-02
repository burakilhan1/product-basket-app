<template>
    <div class="row">
      <div class="card offset-2 col-md-3">
        <div class="card-body text-center d-flex align-items-center">
          <img height="128" @click="$refs.imgFile.click()" :src="product.selectedImage == null ? '/src/assets/addpicture.png' : product.selectedImage" class="img-responsive text-center">
          <input type="file" ref="imgFile" class="form-control" @change="onChange($event)" style="display:none">
        </div>
      </div>
      <div class="col-md-5">
        <div class="col-md-11 card">
          <div class="card-body">
            <form action="">
            <div class="form-group">
              <label>Product Name</label>
              <input type="text" v-model="product.name" class="form-control" placeholder="Enter a name.." required>
            </div>
            <div class="row">
              <div class="form-group col-md-6">
                <label>Count</label>
                <input type="text" v-model="product.count" class="form-control" placeholder="Enter a count.." required>
              </div>
              <div class="form-group col-md-6">
                <label>Price</label>
                <div class="input-group mb-3">
                  <input type="text" v-model="product.price" class="form-control" placeholder="Enter a price.." required>
                  <div class="input-group-append">
                    <span class="input-group-text">$</span>
                  </div>
                </div>
              </div>
            </div>
            <button class="btn btn-outline-info btn-block" @click="addProduct()">Add</button>
            </form>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
import { eventBus } from '../main'

  export default {
    data() {
        return {
            product : {
                selectedImage: null,
                name: null,
                count: null,
                price: null,
                totalPrice:null
            }
        }
    }, 
    methods: {
        onChange(e){
            const imgFile = e.target.files[0]
            this.product.selectedImage = URL.createObjectURL(imgFile)
        },
        addProduct(){
            if ((this.product.name, this.product.count, this.product.price) != null) {
                this.product.totalPrice = this.product.count * this.product.price
                if (this.product.selectedImage == null) {
                    this.product.selectedImage = '/src/assets/no-image.png'
                }
                eventBus.$emit("productAdded", this.product)
                this.product = {
                  selectedImage: null,
                  name: null,
                  count: null,
                  price: null,
                  totalPrice: null
                }
            }
        }
    }
  }
</script>