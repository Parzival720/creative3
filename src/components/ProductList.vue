<template>
  <div class="wrapper">
    <div class="products">
      <div class="product" v-for="product in products" :key="product.id">
        <div @click="selectProduct(product)">
          <div class="info">
            <h1>{{product.name}}</h1>
            <p>{{product.description}}</p>
          </div>
          <div class="image">
            <img :src="'/images/tech/'+product.image">
          </div>
        </div>

        <div class="price">
          <h2>${{product.price}}</h2>
          <button class="auto" @click="addToCart(product)">Add to Cart</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductList',
  props: {
    products: Array
  },
  methods: {
    addToCart(product) {
      this.$root.$data.cart.push(product);
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
a {
    text-decoration: none;
    color: #333;
}

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
  background: #F64C72;
  border-radius: 5px;
  padding: 10px 30px;
  height: 120px;
  text-decoration: none;
}

.info h1 {
  font-size: 17px;
  text-align: center;
}

.info h2 {
  font-size: 17px;
}

.info p {
  margin: 0px;
  font-size: 15px;
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

.auto {
  margin-left: auto;
}
</style>
