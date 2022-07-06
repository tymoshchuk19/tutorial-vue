<template>
  <tutorial-list :items="items"/>
</template>

<script>
  import TutorialList from '../components/TutorialList'
  import axios from 'axios'

  export default {
    name: 'HomeView',

    components: {
      TutorialList,
    },
    created(){
      this.fetchItems();
    },
    data() {
      return {
        items: []
      }
    },
    methods: {
      async fetchItems() {
        const response = await axios.get('https://vue-tutorial-api.herokuapp.com/api/v1/product')
        console.log(response.data)
        this.items = response.data
      }
    },
  }
</script>
