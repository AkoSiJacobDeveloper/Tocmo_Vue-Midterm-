<template>
  <div>
    <ul
      class="d-flex justify-content-center align-items-center p-3 flex-column"
    >
      <li class="mb-2" v-for="(product, index) in products" :key="index">
        <strong>{{ product.name }}</strong> - {{ product.price }}
        <button @click="editProduct(index)">Edit</button>
      </li>
    </ul>
    <div v-if="isEditing">
      <h3>Edit Product</h3>
      <input v-model="editProductData.name" placeholder="Product Name" />
      <input
        type="number"
        v-model="editProductData.price"
        placeholder="Price"
      />
      <textarea
        v-model="editProductData.description"
        placeholder="Description"
      ></textarea>
      <button @click="updateProduct">Update</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    products: Array,
  },
  data() {
    return {
      isEditing: false,
      editProductData: {},
      editIndex: null,
    }
  },
  methods: {
    editProduct(index) {
      this.isEditing = true
      this.editProductData = { ...this.products[index] }
      this.editIndex = index
    },
    updateProduct() {
      this.$emit('update-product', {
        index: this.editIndex,
        product: this.editProductData,
      })
      this.isEditing = false
      this.editProductData = {}
    },
  },
}
</script>
