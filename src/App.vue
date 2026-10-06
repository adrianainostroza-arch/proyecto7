<script setup>
import AppHeader from './components/AppHeader.vue'
import AppFooter from './components/AppFooter.vue'
import ProductList from './components/ProductList.vue'
</script>

<template>
  <v-app>
    <AppHeader />
    <v-main>
      <v-container>
        <ProductList />
      </v-container>
    </v-main>
    <AppFooter />
  </v-app>
</template>
