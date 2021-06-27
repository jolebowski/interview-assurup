<template>
  <div class="products mt-5">
    <h1 class="font-normal md:font-bold text-xl uppercase">Produits</h1>
    <div>
      <div v-for="product in allProducts" :key="product.id">
        <div class="mt-5 pt-0">
          <input type="text"
            class="px-2 py-1 placeholder-gray-400 text-gray-600
            relative bg-white bg-white rounded text-sm border
            border-gray-400 outline-none focus:outline-none focus:ring"
            v-model="product.name"
            />
         </div>
        <textarea class="mt-2 mb-6 px-6 py-3 border rounded-lg mt-3"
         type="text" v-model="product.description"
          placeholder={} rows="7" cols="30">
        </textarea>
      </div>
    </div>

  </div>
</template>
<script>
import { mapGetters } from 'vuex';

export default {
  computed: {
    ...mapGetters('products', ['allProducts']),
  },
};
</script>
<style scoped>
  .products ul {
    padding: 0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
    max-width: 400px;
    margin: 60px auto;
  }
  .products li {
    list-style-type: none;
    background: white;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 1px 3px 5px rgba(0,0,0,0.1);
    cursor: pointer;
    line-height: 1.5em;
  }
  h2{
  text-transform: capitalize;
}
</style>
