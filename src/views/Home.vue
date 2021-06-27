<template>
  <div class="contracts mt-5">
    <h1 class="font-normal md:font-bold text-xl uppercase">Contrats</h1>
    <div>
    <button @click="sortPriceDecrease" class="bg-red-500 hover:bg-red-700 text-white
     py-2 px-4 rounded-full inline-flex">
      <span class="material-icons">
      arrow_downward
      </span>
      Prix
    </button>
    <button @click="sortPriceGrowth" class="bg-red-500 hover:bg-red-700 text-white
     py-2 px-4 rounded-full inline-flex">
      <span class="material-icons">
      arrow_upward
      </span>
      Prix
    </button>
    <button @click="sortGrowthProduct" class="bg-blue-500 hover:bg-blue-700 text-white
    font-bold py-2 px-4 rounded-full inline-flex">
      <span class="material-icons">
      arrow_downward
      </span>
      <span>Produit</span>
    </button>
    <button @click="sortDecreaseProduct" class="bg-blue-500 hover:bg-blue-700
    text-white font-bold py-2 px-4
    rounded-full inline-flex text-cente">
      <span class="material-icons">
        arrow_upward
      </span>
      <span>Produit</span>
    </button>
    <button @click="sortDate" class="bg-yellow-500 hover:bg-yellow-700 text-white
    font-bold py-2 px-4 rounded-full inline-flex">
      <span class="material-icons">
      arrow_downward
      </span>
      <span class="material-icons">
        arrow_upward
      </span>
      <span>Date</span>
    </button>
    </div>
    <div>
      <router-link :to="{name: 'contract', params : { idContract : contract.id,
      idProduct: contract.productId}}"
      class="contract transform hover:scale-110 motion-reduce:transform-none ..."
      v-for="(contract, idx) in allContracts" :key="idx">
        <h2 class="font-normal md:font-bold text-base uppercase"
          v-for="product in allProducts" :key="product.id">
            {{product.id === contract.productId ? product.name : ''}}
          </h2>
          <span class="material-icons mt-5">{{ contract.icon }}</span>
          <h3 class="mt-5">{{ contract.effectiveDate }}</h3>
          <h4 class="mt-5">{{ contract.price }} €</h4>
          <div :class="contract.status === 'PAID' ? 'status-done' : 'status-wait'">
            {{ contract.status }}
          </div>
      </router-link>
    </div>
  </div>
</template>
<script>
import { mapGetters } from 'vuex';

export default {
  computed: {
    ...mapGetters('contracts', ['allContracts']),
    ...mapGetters('products', ['allProducts']),
  },
  methods: {
    sortDecreaseProduct() {
      this.allContracts.sort((a, b) => (a.productId > b.productId ? 1 : -1));
    },
    sortGrowthProduct() {
      this.allContracts.sort((a, b) => (a.productId < b.productId ? 1 : -1));
    },
    sortPriceDecrease() {
      this.allContracts.sort((a, b) => (a.price > b.price ? 1 : -1));
    },
    sortPriceGrowth() {
      this.allContracts.sort((a, b) => (a.price < b.price ? 1 : -1));
    },
    sortDate() {
      this.allContracts.sort((a, b) => (a.effectiveDate - b.effectiveDate ? 1 : -1));
    },
  },
};
</script>
<style scoped>
  .contracts > div {
    padding: 0;
    display: grid;
    grid-template-columns: 1fr 1fr;
    grid-gap: 20px;
    max-width: 400px;
    margin: 30px auto;
  }
  .contract {
    list-style-type: none;
    background: white;
    padding: 30px;
    border-radius: 10px;
    box-shadow: 1px 3px 5px rgba(0,0,0,0.1);
    line-height: 1.5em;
  }
  .status-done {
    border: 1px solid #ccc;
    background: #41b883;
    padding: 0.1rem;
    color: #fff;
    border-radius: 30px;
    cursor: pointer;
    margin-top: 20px;
}
  .status-wait {
    border: 1px solid #ccc;
    background: #FFDC48;
    padding: 0.1rem;
    color: #fff;
    border-radius: 30px;
    cursor: pointer;
    margin-top: 20px;

}
</style>
