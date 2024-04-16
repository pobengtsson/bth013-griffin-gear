<template>
  <v-container fluid>
    <v-row justify="center">
      <v-col cols="12">
        <v-carousel cycle height="600px" hide-delimiter-background show-arrows-on-hover>
          <v-carousel-item v-for="(item, i) in carouselItems" :key="i">
            <v-img :src="item.image" aspect-ratio="1" contain>
              <template v-slot:placeholder>
                <v-row class="fill-height ma-0" align="center" justify="center">
                  <v-progress-circular indeterminate color="grey lighten-5"></v-progress-circular>
                </v-row>
              </template>
              <v-row class="fill-height" align="bottom" justify="center">
                <v-col class="text-h5 white-text text-center" cols="8">
                  <div><strong>{{ item.title }}</strong></div>
                  <div>{{ item.description }}</div>
                </v-col>
              </v-row>
            </v-img>
          </v-carousel-item>
        </v-carousel>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'HomeView',
  data: () => ({
    carouselItems: [
      {
        title: 'Welcome to the Fantasy Creatures Shop',
        description: 'Dive into the enchanting world of Fantasy Creatures Shop, where every corner unveils a new magical being waiting to become your companion. Embark on an adventure with us and find your next mystical friend today!',
        image: './assets/fantasy-creatures-shop.jpeg',
      },
      {
        title: 'How to Care for Your Dragon',
        description: 'Dragons are not just pets; they are loyal companions and formidable guardians. Learn the essentials of dragon care, from the fireproofing your home to the art of communication with these majestic creatures. Ensure your dragon thrives in the modern world with our comprehensive guide.',
        image: './assets/me-and-my-dragon.jpeg',
      },
      {
        title: 'Exclusive Offer: Mythical Creatures',
        description: 'For a fleeting moment, the gates to the extraordinary creatures bazaar are open for you. Seize this chance to adopt a mythical creature at unprecedented prices. Discover beings of legend like the graceful unicorn, the mischievous pixie, or the wise griffin. Enhance your life with magic and mystery now!',
        image: './assets/creatures-bazar-2.jpeg',
      },
    ],
  }),
};
</script>

<style>
.white-text {
  color: white;
}
.v-carousel .v-carousel-item img {
  object-fit: cover; /* Ensure images cover the carousel area without stretching */
}
</style>
