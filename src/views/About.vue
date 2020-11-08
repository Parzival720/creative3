<template>
  <div class="wrapper">
    <div class="header">
      <button class="back" @click="goBack()">Go Back</button>
    </div>
    <div class="product">
        <div class="info">
          <h1>{{product.name}}</h1>
          <p>{{product.description}}</p>
        </div>
        <div class="image">
          <img :src="'/images/tech/'+product.image">
        </div>
        <div class="price">
          <h2>${{product.price}}</h2>
          <button class="auto" @click="addToCart(product)">Add to Cart</button>
        </div>
    </div>
    <h1>Other products you may be interested in:</h1>
    <div class="interested">
        <div v-for="product in relatedProducts" :key="product.id">
          <div class="short" @click="selectProduct(product)">
            <h1>{{product.name}}</h1>
            <img :src="'/images/tech/'+product.image">
          </div>
        </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'About',
  data() {
    return {
      product: this.$root.$data.selected,
    }
  },
  computed: {
    relatedProducts() {
      let relatedIds = this.product.related;
      return this.$root.$data.products.filter((item) => {
        if (relatedIds.includes(item.id)) {
          return item;
        }
      });
    }
  },
  methods: {
    addToCart(product) {
      this.$root.$data.cart.push(product);
    },
    goBack() {
      this.$router.go(-1);
    },
    selectProduct(product) {
      this.$root.$data.selected = product;
      this.product = product;
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

.header {
  display: flex;
  width: 100%;
}

.back {
  background-color: #F64C72;
  color: #fff;
}

.products {
  margin-top: 20px;
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.product {
  border-radius: 5px;
  border: solid 20px #F64C72;
  color: #000;
  margin: 10px;
  margin-top: 50px;
  width: 100%;
  background-color: #97CAEF;
}

.product img {
  height: 200px;
  width: 250px;
  object-fit: cover;
}

.product .image {
  display: flex;
  justify-content: center;
}

.info {
  background: #99738E;
  padding: 10px 30px;
  height: 120px;
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

.interested {
  display: flex;
  flex-wrap: wrap;
  justify-content: flex-start;
  border-radius: 5px;
  border: solid 20px #F64C72;
  color: #000;
  width: 100%;
  background-color: #97CAEF;
  flex-direction: row;
}

.short {
  margin: 10px;
  border: solid 5px #552D67;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  background-color: #99738E;
}

.short h1 {
  font-size: 15px;
}

.short img {
  height: 80px;
  width: 100px;
  object-fit: cover;
}

.auto {
  margin-left: auto;
}
</style>
