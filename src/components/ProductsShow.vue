<template>
  <div class="productscards">
    <div>{{ carts }}</div>
    <div class="itemcard" v-for="item in products" v-bind:key="item.id">
      <!-- <h2>Name: {{ item.title }}</h2>
      <img class="image" :src="item.image" alt="" />
      <p>Price: {{ item.price }}</p>
      <p>Rating: {{ item.rating.rate }}</p>
      <p>Count: {{ item.rating.count }}</p>
      <button @click="addToCars(item)" class="">Add to card</button> -->
      <ProductCard :product="item" />
    </div>
  </div>
</template>
<script>
import ProductCard from "./ProductCard.vue";
export default {
  name: "HelloWorld",
  props: {
    products: Array,
  },
  data() {
    return {
      carts: [],
    };
  },
  methods: {
    addToCars(item) {
      let found = this.carts.find((el) => {
        return el.title == item.title;
      });
      console.log(found);
      if (found) {
        found.quantity += 1;
        return;
      } else {
        let cartItem = {
          title: item.title,
          price: item.price,
          quantity: 1,
        };
        this.carts.push(cartItem);
      }
    },
  },
  components: { ProductCard },
};
</script>
