<template>

  <div class="cart">
   <div class="title">Product Id</div>
    <input class="tinput" v-model="product.product_id" placeholder="Enter Product ID">

    <div class="title">Product Description</div>
    <input class="tinput" v-model="product.product_name" placeholder="Enter Product Description">

    <div class="title">Quantity</div>
    <input class="tinput" v-model.number="product.product_quantity" placeholder="Enter Product Quantity">

    <div class="title">Price</div>
    <input class="tinput" v-model.number="product.product_price" placeholder="Enter Product Price">

    <button class="butt" @click="addProduct">Add Product</button>

    <table class="table">
      <h4 class="table-title">Available Products</h4>
        <tr class="headoftable">
            <th scope="col">ID</th>
            <th scope="col">Description</th>
            <th scope="col">Quantity</th>
            <th scope="col">Price</th>
            <th scope="col">Actions</th>
        </tr>
        <tr v-for="item in cart.items" class="headoftable" :key="index">
          <td>{{item.product_id}}</td>
          <td>{{item.product_name}}</td>
          <td>{{item.product_quantity}}</td>
          <td>{{item.product_price}}</td>
          <button class="btn del" id="btnRemov" @click="removeItem(item)">Remove</button>
          <button class="btn success" @click="addToCart">Add to Cart</button>
        </tr>
    </table>

    <table>
      <h4 class="table-title">Your Shopping Cart</h4>
        <tr class="headoftable">
            <th scope="col">ID</th>
            <th scope="col">Description</th>
            <th scope="col">Quantity</th>
            <th scope="col">Price</th>
            <th scope="col">Actions</th>
        </tr>
       
        <template v-if="checkout">
           <tr v-for="item in cart.items" class="headoftable" :key="row">
          <td>{{item.product_id}}</td>
          <td>{{item.product_name}}</td>
          <td>{{item.product_quantity}}</td>
          <td>{{item.product_price}}</td>
          <button class="btn del" @click="removeFromCart(item)">Delete</button>
        </tr>
        </template>
       
    </table>


    <div class="total" v-if="checkout"><b>Grand Total: {{cartTotal}}</b></div>
  </div>
</template>

<script>
export default {

  data () {
    return {
      checkout: false,
       cart: {
            items: []
        },
       product: {
         product_id:'',
         product_name:'',
         product_quantity:'',
         product_price:''
       },
       shopCart:[]
    }
     
  },
  methods:{
     addProduct: function() {
       if(this.product.product_id === "" || this.product.product_name === "" || this.product.product_quantity === "" || this.product.product_price === ''){
         alert("Please Fill all Inputs");
         return;
       }
       this.cart.items.push(this.product); 
       this.checkout = false;         
      },
      removeItem: function () {
         let index = this.cart.items.indexOf(this.cart.items);
        /*Removes the product from the listOfItems array which st
        ores all the items in the shopping cart */
        this.cart.items.splice(index, 1); //
      },
      addToCart: function() {
        this.shopCart.push(this.product);
        this.checkout = true;
      },
      removeFromCart: function () {
         let row = this.shopCart.indexOf(this.cart.items);
        /*Removes the product from the listOfItems array which st
        ores all the items in the shopping cart */
        this.shopCart.splice(row, 1); //
      }

    },
    
    computed: {
        cartTotal: function() {
            var total = 0;
        
            this.cart.items.forEach(function(item) {
                total += item.product_quantity * item.product_price;
            });

            return total;
        },
    }
  }
</script>


<style scoped>
.cart{
  margin-top: 40px;
  margin-left:10%;
  margin-right: 10%;
}
.table-titles{
    text-align: center;
    margin-top: 20px;
}
.tinput{
  width: 100%;
  margin-top: 10px;
  height: 32px;
  padding-left: 15px;
  font-size: 15px;
}
.butt{
  width: 120px;
  height: 40px;
  background-color: blue;
  margin-top:40px;
  color: white;
  font-size: 16px;
}
table{
  margin-top: 15px;
}
.headoftable{

  background-color: black;
  color: white;
  height: 40px;
}
h4{
  text-align: center;
  color: gray;
  display: inline-block;
  font-size: 20px;
}
th{
  width: 300px;
}
.total{
  font-size: 30px;
  margin-top: 50px;
  color: #000000;
}
#btnRemov{
  text-align: center;

  margin-right: 10px;
}

.success{
  background-color: blue;
  color: white;
  height: 30px;
  width: 80px;
  margin: 12px;
}

.del{
  background-color: red;
  color: white;
  height: 30px;
  width: 80px;
  margin: 12px;
}

.title{
  margin-top: 30px;

}
</style>
