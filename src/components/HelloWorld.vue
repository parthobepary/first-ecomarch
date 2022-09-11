<template>
  <div>
    <h1>Welcome to online shopping</h1>
    <div class="productscards">
      <div class="itemcard" v-for="item in products" v-bind:key="item.id">
        <h2>Name: {{ item.title }}</h2>
        <img class="image" :src="item.image" alt="" />
        <p>Price: {{ item.price }}</p>
        <p>Rating: {{ item.rating.rate }}</p>
        <p>Count: {{ item.rating.count }}</p>
        <button @click="hello(item.id)" class="">Add to card</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",

  data() {
    return {
      products: [],
    };
  },
  mounted() {
    this.axios.get("https://fakestoreapi.com/products").then((res) => {
      this.products = res.data;
    });
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style></style>
