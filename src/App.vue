<template>
  <div id="app">
    <div class="navbar">
      <div>
        <h1>Onlone shope</h1>
      </div>
      <nav>
        <router-link class="navlink" to="/">Home</router-link> |
        <router-link class="navlink" to="/carts">Cart</router-link> |
        <router-link class="navlink" to="/about">About</router-link>
      </nav>
    </div>
    <div class="contain">
      <router-view />
    </div>
  </div>
</template>

<style scoped>
h1 {
  color: rgb(145, 35, 35);
}
.contain {
  text-align: center;
}
</style>
