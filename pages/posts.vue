<script setup>

import { ref } from 'vue';
const pets = ref([]);


const response = await fetch('https://api.doggiepedia.org/random?count=10');
pets.value = await response.json();



</script>




<template>
    <v-row>
        <v-col>
    <h1 class="text-3xl text-center">Post Page </h1>

        </v-col>
    </v-row>
    <v-row >
        <v-col cols="12" md="6" lg="3" xl="3" v-for="{image, name, about_trimmed} in pets" :key="name">

    <v-card
    class="mx-auto"
    max-width="344"
    hover
  >
  <v-img
      class="align-end text-white"
      height="200"
      :src="`https://assets.doggiepedia.org/dogs/${image}`"
      cover
    > <v-card-title>
        {{ name}}
      </v-card-title>
</v-img>

    <v-card-item>
     

      <v-card-subtitle>
        Descripcion
      </v-card-subtitle>
    </v-card-item>

    <v-card-text>
     {{ about_trimmed}}
    </v-card-text>
    <v-btn
        append-icon="mdi-chevron-right"
        color="red-lighten-2"
        text="Ver mas"
        variant="outlined"
        block
      ></v-btn>
  </v-card>

</v-col >

    </v-row>
    

  

    
  </template>
  