<template>
  <v-container>
    <v-row>
      <v-col cols="12" sm="6" md="4" v-for="creature in creatures" :key="creature.id">
        <v-card @click="showDetails(creature)" class="mx-auto" max-width="344" outlined>
          <v-img :src="creature.image" class="white--text align-end">
          </v-img>
          <v-card-title>{{ creature.name }}</v-card-title>
          <v-card-subtitle class="pb-0">{{ creature.type }}</v-card-subtitle>
          <v-card-text class="text--primary">
            <div>{{ creature.price | currency }}</div>
            <v-chip small color="{rarityColor(creature.rarity)}" dark>{{ creature.rarity }}</v-chip>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-dialog v-model="detailsDialog" max-width="600px">
      <v-card>
        <v-img :src="selectedCreature.image"></v-img>
        <v-card-title>{{ selectedCreature.name }}</v-card-title>
        <v-card-subtitle>{{ selectedCreature.type }} - {{ selectedCreature.rarity }}</v-card-subtitle>
        <v-card-text>{{ selectedCreature.description }}</v-card-text>
        <v-card-actions>
          <v-btn color="blue darken-1" text @click="detailsDialog = false">Close</v-btn>
          <v-btn color="green darken-1" text>Add to Cart</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </v-container>
</template>

<script>
export default {
  name: 'CatalogView',
  data: () => ({
    detailsDialog: false,
    selectedCreature: {},
    creatures: [
      {
        id: 1,
        name: 'Fire Dragon',
        type: 'Dragon',
        rarity: 'Rare',
        price: 500,
        description: 'A majestic dragon capable of breathing fire. Known for its wisdom and temper.',
        image: 'assets/fire-dragon.jpeg',
      },
      {
        id: 2,
        name: 'Norwegian Ridgeback',
        type: 'Dragon',
        rarity: 'Uncommon',
        price: 600,
        description: 'Noted for the distinctive ridge running down its back, this dragon is fiercely protective of its territory.',
        image: 'assets/norwegian-ridgeback.jpeg',
      },
      {
        id: 3,
        name: 'Hungarian Horntail',
        type: 'Dragon',
        rarity: 'Very Rare',
        price: 800,
        description: 'Considered one of the most dangerous dragon breeds, it has yellow eyes, bronze horns, and spiky tails.',
        image: 'assets/hungarian-horntail.jpeg',
      },
      {
        id: 4,
        name: 'Swedish Short-Snout',
        type: 'Dragon',
        rarity: 'Rare',
        price: 700,
        description: 'This dragon is known for its silvery blue scales and short snout, emitting a bright blue flame.',
        image: 'assets/swedish-short-snout.jpeg',
      },
      {
        id: 5,
        name: 'Chinese Fireball',
        type: 'Dragon',
        rarity: 'Uncommon',
        price: 650,
        description: 'Also known as the Liondragon, it has a highly aggressive nature and a tendency to emit large fireballs.',
        image: 'assets/chinese-fireball.jpeg',
      },
      {
        id: 6,
        name: 'Peruvian Vipertooth',
        type: 'Dragon',
        rarity: 'Common',
        price: 450,
        description: 'Smallest of the dragon breeds, it has smooth, copper-colored scales and venomous fangs.',
        image: 'assets/peruvian-vipertooth.jpeg',
      },
      {
        id: 7,
        name: 'Romanian Longhorn',
        type: 'Dragon',
        rarity: 'Rare',
        price: 750,
        description: 'Features dark green scales and long, glittering golden horns used in potion-making.',
        image: 'assets/romanian-longhorn.jpeg',
      },
      {
        id: 8,
        name: 'Ukrainian Ironbelly',
        type: 'Dragon',
        rarity: 'Very Rare',
        price: 900,
        description: 'The largest breed of dragon, with metallic grey skin and deep red eyes, known for its immense strength.',
        image: 'assets/ukrainian-ironbelly.jpeg',
      },
      {
        id: 9,
        name: 'Hebridean Black',
        type: 'Dragon',
        rarity: 'Uncommon',
        price: 550,
        description: 'Native to the Hebrides Islands, it is dark with rough scales, purple eyes, and a row of sharp ridges along its back.',
        image: 'assets/hebridean-black.jpeg',
      },
      {
        id: 10,
        name: 'Antipodean Opaleye',
        type: 'Dragon',
        rarity: 'Rare',
        price: 700,
        description: 'It possesses iridescent scales and glittering, multicolored, pupil-less eyes that have enchanted many.',
        image: 'assets/antipodean-opaleye.jpeg',
      },
      {
        id: 11,
        name: 'Catalonian Firestarter',
        type: 'Dragon',
        rarity: 'Common',
        price: 500,
        description: 'A mischievous breed known for igniting small fires, it sports a vibrant red and yellow patterned body.',
        image: 'assets/catalonian-firestarter.jpeg',
      },
      {
        id: 12,
        name: 'Siberian Icebreather',
        type: 'Dragon',
        rarity: 'Very Rare',
        price: 850,
        description: 'With its icy blue scales and ability to exhale a sub-zero breath, it thrives in cold environments.',
        image: 'assets/siberian-icebreather.jpeg',
      },
      {
        id: 13,
        name: 'Alpine Ridge-Walker',
        type: 'Dragon',
        rarity: 'Uncommon',
        price: 600,
        description: 'Known for navigating steep mountain ridges with ease, its scales shimmer like fresh snow under the sun.',
        image: 'assets/alpine-ridge-walker.jpeg',
      },
    ],

  }),
  methods: {
    showDetails(creature) {
      this.selectedCreature = creature;
      this.detailsDialog = true;
    },
  },
  filters: {
    currency(value) {
      const formatter = new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD',
      });
      return formatter.format(value);
    },
    rarityColor(rarity) {
      switch (rarity.toLower()) {
        case 'uncommon': return 'amber'
        default:
          return "amber"
      }
    }
  },
};
</script>

<style scoped>
.v-card-title,
.v-card-subtitle {
  color: midnightblue !important;
}
</style>
