<template>
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
</template>
<script>
export default {
  name: "HelloWorld",
  props: {
    products: Array,
  },
};
</script>
