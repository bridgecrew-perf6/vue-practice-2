<template>
  <div>
    <ProductItem
      v-for="product in products"
      :key="product.id"
      :product="product"
    />
  </div>
</template>

<script>
import ProductItem from "./ProductItem.vue";
export default {
  name: "product-list",
  props: {
    products: {
      type: Array,
      default: () => {
        return [];
      },
    },
  },
  components: {
    ProductItem,
  },
};
</script>

<style></style>
