<template>
  <div>
    <h1>Product Manager</h1>
    <ProductForm @add-product="addProduct" />
    <ProductList :products="products" @update-product="updateProduct" />
  </div>
</template>

<script>
import ProductForm from './ProductForm.vue'
import ProductList from './ProductList.vue'

export default {
  components: { ProductForm, ProductList },
  data() {
    return {
      products: [],
    }
  },
  methods: {
    addProduct(product) {
      this.products.push(product)
    },
    updateProduct({ index, product }) {
      this.$set(this.products, index, product)
    },
  },
}
</script>
