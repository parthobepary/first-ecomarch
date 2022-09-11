<template>
  <div>
    <h1>Welcome to online shopping</h1>
    <div>
      <button @click="showAll">All</button>
      <button @click="showAllLowprice(10)">0-10</button>
      <button @click="showAllLowprice(30)">10-30</button>
    </div>
    <div class="productscards">
      <div class="itemcard" v-for="item in products" v-bind:key="item.id">
        <h2>Name: {{ item.title }}</h2>
        <img class="image" :src="item.image" alt="" />
        <p>Price: {{ item.price }}</p>
        <p>Rating: {{ item.rating.rate }}</p>
        <p>Count: {{ item.rating.count }}</p>
        <button class="">Add to card</button>
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
      shortedData: [],
    };
  },
  methods: {
    showAll() {
      this.axios.get("https://fakestoreapi.com/products").then((res) => {
        this.products = res.data;
      });
    },
    showAllLowprice(value) {
      const valus = this.products;
      const result = valus.filter((element) => element?.price <= value);
      this.products = result;
    },
  },
  mounted() {
    this.axios.get("https://fakestoreapi.com/products").then((res) => {
      this.products = res.data;
    });
  },

  created() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style></style>
