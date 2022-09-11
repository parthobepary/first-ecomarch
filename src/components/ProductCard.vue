<template>
  <div>
    <h2>Name: {{ product.title }}</h2>
    <img class="image" :src="product.image" alt="" />
    <p>Price: {{ product.price }}</p>
    <p>Rating: {{ product.rating.rate }}</p>
    <p>Count: {{ product.rating.count }}</p>
  </div>
</template>
<script>
export default {
  props: {
    product: { type: Object, required: true },
  },
};
</script>
