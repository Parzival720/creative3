<template>
<div class="wrapper">
  <div class="products">
    <div class="product" v-for="product in cartItems" :key="product.id">
      <div @click="selectProduct(product)">
        <div class="info">
          <h1>{{product.name}}</h1>
          <p>{{product.country}}</p>
        </div>
        <div class="image">
            <img :src="'/images/tech/'+product.image">
        </div>
      </div>
      <div class="price">
        <h2>${{product.price}}</h2>
        <button class="auto" @click="removeFromCart(product)">Remove from Cart</button>
      </div>
    </div>
  </div>
  <div class="cart-info-wrapper">
    <div class="cart-info">
      <div v-if="emptyCart">
        <p>There are no items in your cart. Go check out the collection!</p>
      </div>
      <div v-else>
        <div class="total">
          <p>Total: ${{totalCost}}</p>
        </div>
      </div>
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
    },
    emptyCart() {
      if (this.$root.$data.cart.length == 0) {
        return true;
      }
      return false;
    },
    totalCost() {
      return this.$root.$data.cart.reduce((total, item) => { return total + item.price; }, 0).toFixed(2);
    }
  },
  methods: {
    removeFromCart(product) {
      var index = this.$root.$data.cart.indexOf(product);
      this.$root.$data.cart.splice(index, 1);
    },
    selectProduct(product) {
      console.log(product);
      this.$root.$data.selected = product;
      this.$router.push('/about');
    }
  }
}
</script>

<style scoped>
.wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
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
  border: solid 5px #F64C72;
  border-radius: 5px;
  background-color: #fff;
  width: 500px;
  height: 50px;
  display: flex;
  justify-content: space-around;
}

.cart-info {
  display: flex;
}

.total {

  display: flex;
  justify-self: flex-end;
  margin-left: auto;
}

.auto {
  margin-left: auto;
}
</style>
