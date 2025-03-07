<template>
  <v-app>
    <v-app-bar app color="deep-purple accent-4" dark>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Fantasy Creatures Shop</v-toolbar-title>
      <v-spacer></v-spacer>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" app>
      <v-list>
        <v-list-item link :to="{ name: 'home' }">
          <v-icon>mdi-home</v-icon>
          <v-list-item-title>Home</v-list-item-title>
        </v-list-item>
        <v-list-item link :to="{ name: 'catalog' }">
          <v-icon>mdi-book-open-page-variant</v-icon>
          <v-list-item-title>Catalog</v-list-item-title>
        </v-list-item>
        </v-list>
    </v-navigation-drawer>

    <v-main>
      <router-view></router-view>
    </v-main>

    <v-footer fixed padless>
      <v-col class="text-center">©2024-2025 Fantasy Creatures Shop</v-col>
    </v-footer>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue'
  const drawer = ref(false)
</script>
