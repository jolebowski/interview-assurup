<template>
  <div id="containerApp">
    <nav id="nav">
      <router-link :to="{ name: 'Home'}" exact>Accueil</router-link> |
      <router-link :to="{ name: 'Products'}">Produits</router-link>
      <transition
        enter-active-class="animate__animated animate__fadeInLeft"
        leave-active-class="animate__animated animate__fadeOutLeft"
        mode="out-in"
      >
      <router-view v-slot="{ Component}">
        <component :is="Component"></component>
      </router-view>
      </transition>
    </nav>
    <div class="flex flex-col">
      <div class="text-base font-semibold font-serif">
        &copy; Copyright {{new Date().getFullYear()}}
      </div>
    </div>
  </div>
</template>
<script>
import contracts from '@/assets/data/contracts.json';
import products from '@/assets/data/products.json';

export default {
  mounted() {
    this.$store.dispatch('contracts/setValue', { list: contracts });
    this.$store.dispatch('products/setValue', { list: products });
  },
};
</script>
<style>
#containerApp {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav a.router-link-exact-active {
  color: #0063E3;
}
#nav {
  padding: 30px;
}
#nav a {
  font-weight: bold;
  color: #2c3e50;
  font-size: 1rem;
}
</style>
