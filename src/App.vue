<template>
  <div id="app">
    <div id="menu">
      <div id="left">
      <span class="form-inline">
        <input class="form-control mr-sm-2" type="search" placeholder="Search" aria-label="Search">
        <button class="btn my-2 my-sm-0" type="submit">
          <img src="../images/search.png" width=20 height=20/>
        </button>
      </span>
      </div>
      <div id="brand">
        <router-link to="/">
          <img src="../images/cpu.png">
        </router-link>
        <h1>Gleek Skwad</h1>
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
        <a class="github-link" href='https://github.com/Parzival720/creative3' target='_blank'>
          <img src="../images/github.png" class="small-icon"  width="50" height="30">
          Link to GitHub repository
        </a>
        <div class='copyright'>
          <p>All Content Copyrighted by Recursive Outfitters</p>
        </div>
        Icons made by <a href="https://www.flaticon.com/authors/freepik" title="Freepik">Freepik</a> from <a href="https://www.flaticon.com/" title="Flaticon"> www.flaticon.com</a>
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
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@500&display=swap');
* {
  box-sizing: border-box;
}

body {
  margin: 50px 100px;
  background-color: #2F2FA2 !important;
}


#menu {
  display: grid;
  padding: 20px;
  border-radius: 5px;
  border: solid 20px #F64C72;
  grid-template-columns: 1fr 1fr 1fr;
  grid-column-gap: 5px;
  grid-template-areas: "left brand side";
  margin-bottom: 50px;
  background-color: #99738E !important;
}

#menu a {
  color: #B84901;
}

#brand {
  grid-area: brand;
  display: flex;
  justify-content: center;
  flex-direction: column;
  font-family: 'Oswald', sans-serif;
}

#brand h1 {
  padding-left: 20px;
}

#brand img {
  height: 200px;
}

#left {
  grid-area: left;
  display: flex;
  justify-content: flex-start;
  align-self: center;
}

#side {
  grid-area: side;
  display: flex;
  justify-content: flex-end;
  align-self: center;
}

#side img {
  width: 50px;
}

.menu-item {
  display: flex;
  flex-direction: column;
  color: #242582
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
