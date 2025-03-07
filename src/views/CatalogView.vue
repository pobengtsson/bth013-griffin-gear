<template>
  <v-container>
    <v-row>
      <v-col cols="12" sm="6" md="4" v-for="creature in creatures" :key="creature.id">
        <v-card @click="showDetails(creature)" class="mx-auto" max-width="30vw" outlined>
          <v-img :src="creature.image" class="white--text align-end">
          </v-img>
          <v-card-title>{{ creature.name }}</v-card-title>
          <v-card-subtitle class="pb-0">{{ creature.type }}</v-card-subtitle>
          <v-card-text class="text--primary">
            <div>{{ currency(creature.price) }}</div>
            <v-chip small :color="rarityColor(creature.rarity)" dark>{{ creature.rarity }}</v-chip>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-dialog v-model="detailsDialog" max-width="60vw">
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

<script setup>
import { ref, reactive } from 'vue'
import creatures from '@/data/creatures'

const detailsDialog = ref(false)
const selectedCreature = reactive({})

const showDetails = (creature) => {
  Object.assign(selectedCreature, creature)
  detailsDialog.value = true;
}

function currency(value) {
      const formatter = new Intl.NumberFormat('en-US', {
        style: 'currency',
        currency: 'USD',
      });
      return formatter.format(value)
    }
const rarityColor = (rarity) => {
  switch (rarity.toLowerCase()) {
    case 'common':
      return 'grey';
    case 'uncommon':
      return 'green';
    case 'rare':
      return 'blue';
    case 'very rare':
      return 'purple';
    default:
      return 'grey';
  }
}
</script>

<style scoped>
.v-card-title,
.v-card-subtitle {
  color: midnightblue !important;
}
</style>
