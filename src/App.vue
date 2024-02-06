<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      email: ''
    }
  },
  mounted() {
    axios.get('https://flynn.boolean.careers/exercises/api/random/mail')
      .then((response) => {
        this.email = response.data.response;
        console.log(this.email);
      })
  }
}
</script>

<template></template>

<style></style>
