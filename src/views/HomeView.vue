<template>
  <v-container>
    <v-carousel cycle interval="5000" height="80vh" hide-delimiters show-arrows="hover">
      <v-carousel-item v-for="(item, i) in carouselItems" :key="i">
        <v-img :src="item.image">
          <template v-slot:placeholder>
            <v-row class="fill-height ma-0" justify="center">
              <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
            </v-row>
          </template>
          <template v-slot:default>
            <v-container>
              <v-spacer></v-spacer>
              <v-sheet rounded class="d-flex align-center justify-center flex-wrap text-center mx-auto px-4"
                style="background: rgba(55, 33, 55, 0.4);">
                <div style="color: gainsboro">
                  <h3>{{ item.title }}</h3>
                  <p>{{ item.description }}</p>
                </div>
              </v-sheet>
            </v-container>
          </template>
        </v-img>
      </v-carousel-item>
    </v-carousel>
  </v-container>
</template>

<script setup>
import carouselItems from '@/data/carouselitems'

</script>

<style>
.white-text {
  color: white;
}
.v-carousel .v-carousel-item img {
  object-fit: cover; /* Ensure images cover the carousel area without stretching */
}
</style>
