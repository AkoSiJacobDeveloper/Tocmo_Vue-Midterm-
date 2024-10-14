<template>
  <div>
    <h1 class="fw-bold mb-2">Products</h1>
    <ProductManager />
  </div>
</template>

<script>
import ProductManager from '../components/ProductManager.vue'

export default {
  components: {
    ProductManager,
  },
}
</script>
