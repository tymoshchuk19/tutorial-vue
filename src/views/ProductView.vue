<template>
  <v-container>
    <genui-form :object="formSchema"></genui-form>
  </v-container>
</template>
<script>
import axios from 'axios'
import GenuiForm from '../components/GenuiForm'
export default {
  name: 'TutorialList',
  props: ['items'],
  components: {
    GenuiForm,
  },
  created(){
    this.getProduct();
  },
  data: () => ({
    formSchema: []
  }),
  methods: {
      async getProduct() {
        var res = [
        {
          name: 'name',
          type: 'text',
          label: 'Name',
          placeholder: 'Enter your name',
          required: true,
        },
        {
          name: 'price',
          type: 'number',
          label: 'Price',
          placeholder: 'Enter your price',
          required: true,
        },
        {
          name: 'quantity',
          type: 'number',
          show: false,
          label: 'Quantity',
          placeholder: 'Enter your quantity',
          required: true,
        }]
        if(this.$route.params.id){
          const response = await axios.get('https://vue-tutorial-api.herokuapp.com/api/v1/product/' + this.$route.params.id)
          res[0].value = response.data.name
          res[1].value = response.data.price
          res[2].value = response.data.quantity
        }
        this.formSchema = res;
      },
  }
}
</script>
