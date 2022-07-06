<template>
  <v-container>
    <genui-slot v-for="field in object" :key="field.name" :label="field.name">
      <template v-slot:value>
        <v-text-field
          v-if="field.type === 'password'"
          outlined
          dense
          hide-details
          :placeholder="field.placeholder"
          v-model="field.value"
          :append-icon="field.show ? 'mdi-eye' : 'mdi-eye-off'"
          @click:append="field.show = !field.show"
          :type="field.show ? 'text' : 'password'"
          >
        </v-text-field>
        <v-text-field
          v-else-if="field.type === 'email' || field.type === 'text'"
          outlined
          dense
          hide-details
          :placeholder="field.placeholder"
          v-model="field.value"
          >
        </v-text-field>
        <v-text-field
          v-else-if="field.type === 'number'"
          outlined
          dense
          hide-details
          :placeholder="field.placeholder"
          type="number"
          v-model="field.value"
          >
        </v-text-field>
      </template>
      <template v-if="field.required" v-slot:validator>
        <v-icon color="green">mdi-checkbox-marked-circle</v-icon>
      </template>
    </genui-slot>
    <v-row>
      <v-col cols="11" align="right">
        <genui-submit :object="object" />
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import GenuiSlot from './GenuiSlot'
import GenuiSubmit from '../components/GenuiSubmit.vue'
  export default {
    name: 'GenuiForm',
    props: ['object'],
    components: {
      GenuiSlot,
      GenuiSubmit,
    },
    data: () => ({
    }),
  }
</script>
