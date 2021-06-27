<template>
    <div class="mt-5">
      <div>
        <h2 class="font-normal md:font-bold text-base uppercase"
          v-for="product in allProducts" :key="product.id">
          {{product.id == idProduct ? product.name : ''}}
        </h2>
      </div>
      <div>
        <div class="font-normal md:font-bold text-base uppercase"
            v-for="contract in allContracts" :key="contract.id">
            <div v-if="contract.id == idContract">
              <h3 class="mt-5">{{ contract.effectiveDate }}</h3>
              <h4 class="mt-5">{{ contract.price }} €</h4>
              <div class="mt-5 font-extrabold text-xl">
                {{ contract.status }}
              </div>
            </div>
        </div>
      </div>
    </div>
</template>

<script>
import { mapGetters } from 'vuex';

export default {
  props: ['idContract', 'idProduct'],
  computed: {
    ...mapGetters('products', ['allProducts']),
    ...mapGetters('contracts', ['allContracts']),
  },
};
</script>
