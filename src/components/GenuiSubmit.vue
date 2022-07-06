<template>
    <v-btn
        v-if="!object.loading"
        @click="submit"
        :loading="object.loading"
        color="primary"
        >
        Submit
    </v-btn>
</template>
<script>
import axios from 'axios'
export default {
    name: "GenuiSubmit",
    props: ["object"],
    methods: {
        submit: function () {
            var newObject = {};
            for(var i = 0; i < this.object.length; i++) {
                newObject[this.object[i].name] = this.object[i].value;
            }
            axios.post('https://vue-tutorial-api.herokuapp.com/api/v1/' + this.$route.name, newObject)
                .then(() => {
                    if(this.$route.name === 'signup') this.$router.push('/login');
                    else this.$router.push('/');
                })
                .catch(function (error) {
                    console.log(error);
                });
        },
    },
    
}
</script>
