<template>
  <div>
    <h1>Welcome to online shopping</h1>
    <div>
      <button @click="showAllLowprice(30)">10-30</button>
      <button @click="showAllLowprice(10)">0-10</button>
      <button @click="showAll">All</button>
      <div class="margin">
        <input v-model="inputValue" type="number" />
        <button @click="inputSearch">Search</button>
      </div>
    </div>
    <div>
      <productsData :products="shortedData"></productsData>
    </div>
  </div>
</template>

<script>
import productsData from "../components/ProductsShow.vue";
export default {
  name: "HelloWorld",
  components: {
    productsData,
  },
  data() {
    return {
      products: [],
      shortedData: [],
      inputValue: "",
    };
  },
  watch: {
    inputValue(newVal, OldVal) {
      console.log(newVal, "new");
      console.log(OldVal, "old");
    },
  },
  methods: {
    showAll() {
      this.shortedData = [...this.products];
    },
    showAllLowprice(value) {
      const valus = this.products;
      const result = valus.filter((element) => element?.price <= value);
      this.shortedData = [...result];
    },
    // search by input

    inputSearch() {
      const rating = this.inputValue;
      const valus = this.products;
      const result = valus.filter((element) => element?.rating?.rate > rating);
      this.shortedData = [...result];
    },
    init() {
      this.axios.get("https://fakestoreapi.com/products").then((res) => {
        this.products = res.data;
        this.shortedData = [...this.products];
      });
    },
  },
  mounted() {
    this.init();
  },

  created() {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style></style>
