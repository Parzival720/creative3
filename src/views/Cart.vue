<template>
<div class="wrapper">
  <div class="products">
    <div class="product" v-for="product in cartItems" :key="product.id">
      <div class="info">
        <h1>{{product.name}}</h1>
        <p>{{product.country}}</p>
      </div>
      <div class="image">
        <img :src="'/images/products/'+product.image">
      </div>
      <div class="price">
        <h2>{{product.price}}</h2>
        <button class="auto" @click="removeFromCart(product)">Remove from Cart</button>
      </div>
    </div>
  </div>
  <div class="cart-info-wrapper">
    <div class="cart-info">
    </div>
  </div>
</div>

</template>

<script>
export default {
  name: 'Cart',
  computed: {
    cartItems() {
      return this.$root.$data.cart;
    }
  },
  methods: {
    removeFromCart(product) {
      var index = this.$root.$data.cart.indexOf(product);
      this.$root.$data.cart.splice(index, 1);
    }
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  border: 1px solid #fff;
  border-radius: 5px;
  color: #000;
  margin: 10px;
  margin-top: 50px;
  width: 250px;
}

.product img {
  height: 200px;
  width: 250px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
  margin-bottom: 5px;
}

.info {
  background: #97CAEF;
  border-radius: 5px;
  padding: 10px 30px;
  height: 70px;
}

.info h1 {
  font-size: 16px;
  text-align: center;
}

.info h2 {
  font-size: 14px;
}

.info p {
  margin: 0px;
  font-size: 10px;
}


.price {
  display: flex;
  padding-left: 25px;
  background-color: #552D67;
  color: #fff;
}

button {
  height: 50px;
  border-radius: 5px;
  background: #000;
  color: white;
  border: none;
  margin-top: 5px;
  margin-right: 20px;
}

.cart-info-wrapper {
  background-color: #fff;
  width: 500px;
  height: 50px;
  display: flex;
  justify-content: space-around;
}

.auto {
  margin-left: auto;
}
</style>
