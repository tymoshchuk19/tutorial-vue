<template>
  <v-container>
    <v-row>
      <v-col cols="6">
        Name
      </v-col>
      <v-col cols="2">
        Price
      </v-col>
      <v-col cols="2">
        Quantity
      </v-col>
      <v-col cols="2">
        Edit
      </v-col>
      
    </v-row>
    <v-row v-for="item in items" :key="item._id">
      <v-col cols="6">
        {{ item.name }}
      </v-col>
      <v-col cols="2">
        {{ item.price }}
      </v-col>
      <v-col cols="2">
        {{ item.quantity }}
      </v-col>
      <v-col cols="2">
        <v-btn color="yellow" @click="$router.push('/product/' + item._id)">Edit</v-btn>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="3" sm="12">
        <v-btn color="green" @click="$router.push('/product')">add item</v-btn>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'TutorialList',
    props: ['items'],
    data: () => ({
    }),
  }
</script>
