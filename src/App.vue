<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      email: []
    }
  },
  mounted() {
    for (let i = 0; i < 10; i++) {
      axios.get('https://flynn.boolean.careers/exercises/api/random/mail')
        .then((response) => {
          console.log(response.data.response);
          this.email.push(response.data.response);
          console.log(this.email);

        })
    }
  }

}
</script>

<template></template>

<style></style>
