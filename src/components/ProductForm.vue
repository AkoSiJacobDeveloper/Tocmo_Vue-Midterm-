<template>
  <div class="container">
    <div class="d-flex justify-content-center">
      <form @submit.prevent="submitForm">
        <div class="d-flex flex-column gap-2">
          <input v-model="productName" placeholder="Product Name" required />
          <input type="number" v-model="price" placeholder="Price" required />
          <textarea
            v-model="description"
            placeholder="Description"
            required
          ></textarea>
          <button
            class="border-0 p-2 fw-bold rounded-1 bg-black text-white"
            type="submit"
          >
            Add Product
          </button>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      productName: '',
      price: '',
      description: '',
    }
  },
  methods: {
    submitForm() {
      const newProduct = {
        name: this.productName,
        price: this.price,
        description: this.description,
      }
      this.$emit('add-product', newProduct)
      this.productName = ''
      this.price = ''
      this.description = ''
    },
  },
}
</script>
