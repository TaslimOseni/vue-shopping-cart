<template>
  <div class="calculator">

    <div class="title">Product Id</div>
    <input class="tinput" v-model="message" placeholder="Enter Product ID">

    <div class="title">Product Description</div>
    <input class="tinput" v-model="message" placeholder="Enter Product Description">

    <div class="title">Quantity</div>
    <input class="tinput" v-model="message" placeholder="Enter Product Quantity">

    <div class="title">Price</div>
    <input class="tinput" v-model="message" placeholder="Enter Product Price">

    <button class="butt">Add Product</button>

    <table>
      <h4>Available Products</h4>
        <tr class="headoftable">
            <th>ID</th>
            <th>Description</th>
            <th>Quantity</th>
            <th>Price</th>
            <th>Actions</th>
        </tr>
    </table>

    <table>
      <h4>Your Shopping Cart</h4>
        <tr class="headoftable">
            <th>ID</th>
            <th>Description</th>
            <th>Quantity</th>
            <th>Price</th>
            <th>Actions</th>
        </tr>
    </table>


    <div class="total"><b>Grand Total: 0</b></div>


  </div>
</template>

<script>
export default {
  data() {
    return {
      
    }
  },
  methods: {
    
  }
}


</script>

<style scoped>

.calculator{
  margin-top: 40px;
  margin-left: 280px;
  margin-right: 300px;
}

.title{
  font-size: 18px;
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
  color: black;
  display: inline-block;
  font-size: 20px;
  horizontal-align: middle;
}

th{
  width: 200px;
}

.total{
  font-size: 30px;
  margin-top: 50px;
  color: #000000;
}


</style>