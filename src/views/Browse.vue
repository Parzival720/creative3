<template>
<div>
  <div class="pure-menu pure-menu-horizontal">
    <h1>Filter Products by Price Range!</h1>
    <ul class="pure-menu-list">
      <li class="pure-menu-item"><a @click="select(10)" href="#" class="pure-menu-link">&lt; 10</a></li>
      <li class="pure-menu-item"><a @click="select(50)" href="#" class="pure-menu-link">&lt; 50</a></li>
      <li class="pure-menu-item"><a @click="select(100)" href="#" class="pure-menu-link">&lt; 100</a></li>
      <li class="pure-menu-item"><a @click="select(1000)" href="#" class="pure-menu-link">&lt; 1000</a></li>
    </ul>
  </div>
  <ProductList :products="products" />
</div>
</template>

<script>
import ProductList from "../components/ProductList.vue"
export default {
  name: 'Browse',
  components: {
    ProductList
  },
  data() {
    return {
      priceMax: 0,
    }
  },
  computed: {
    products() {
      return this.$root.$data.products.filter(product => product.price < this.priceMax);
    }
  },
  methods: {
    select(priceMax) {
      this.priceMax = priceMax;
    }
  }
}
</script>

<style>
  .pure-menu {
    width: 400px;
    padding: 10px;
    background-color: #99738E;
    border: 5px solid #F64C72;
    border-radius: 5px;
  }
</style>
