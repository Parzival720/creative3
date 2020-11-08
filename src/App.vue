<template>
  <div id="app">
    <div id="menu">
      <div id="brand">
        <router-link to="/">
          <img src="../images/logo.png">
        </router-link>
      </div>
      <div id="side">
        <router-link to="/browse">
          <div class="menu-item browse">
            <img src="../images/globe.png">
            <p>Browse</p>
          </div>
        </router-link>
        <router-link to="/cart">
          <div class="menu-item">
            <img src="../images/love.png">
            <p>{{itemsInCart}} items</p>
          </div>
        </router-link>
      </div>
    </div>
    <router-view />
    <div id="gitFooter" class="footer-container">
      <div class='footer'>
        <a class="github-link" href='https://github.com/BYU-CS-260-Winter-2020/lab-3b-grocery-store-Parzival720' target='_blank'>
          <img src="../images/github.png" class="small-icon"  width="50" height="30">
          Link to GitHub repository
        </a>
        <div class='copyright'>
          <p>All Content Copyrighted by Recursive Outfitters</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'App',
  computed: {
    itemsInCart() {
      return this.$root.$data.cart.length;
    }
  },
}
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 50px 100px;

}

#menu {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "none brand side";
  margin-bottom: 50px;
}

#menu a {
  color: #B84901;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
}

#brand img {
  height: 200px;
}

#side {
  grid-area: side;
  display: flex;
  justify-content: flex-end;
}

#side img {
  width: 50px;
}

.menu-item {
  display: flex;
  flex-direction: column;
}

.menu-item p {
  margin: 0px;
}

.browse {
  margin-right: 50px;
}

.footer-container {
  display: flex;
  justify-content: center;
  align-items: center;
}

.footer {
  flex-grow: 1;
  height: 300px;
  display: flex;
  align-items: center;
  flex-direction: column;
  font-family: "Trebuchet MS", sans-serif;
}

.copyright {
  text-align: center;
  border-radius: 5px;
  /* border: 5px solid #5D6063; */
  font-family: "Lucida Bright", "Brush Script MT", sans-serif;
  font-size: 10px;
  display: flex;
  flex: 1;
  justify-content: center;
}

.github-link:link,
.github-link:visited {
  display: block;
  text-decoration: none;
  color: #333;
  font-weight: bold;
  padding: 1em;
  text-align: center;
  border-radius: 0.25em;
}

.github-link:hover,
.github-link:visited:hover {
  color: #add8e6;
}

.github-link:active,
.github-link:visited:active {
  color: #add8e6;
}

.small-icon {
  display: inline-block;
  align: top;
}
</style>
