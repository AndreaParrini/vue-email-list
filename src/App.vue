<script>
import axios from 'axios';

export default {
  name: 'App',
  data() {
    return {
      emails: []
    }
  },
  mounted() {
    for (let i = 0; i < 10; i++) {
      axios.get('https://flynn.boolean.careers/exercises/api/random/mail')
        .then((response) => {
          console.log(response.data.response);
          this.emails.push(response.data.response);
          console.log(this.emails);

        })
    }
  }

}
</script>

<template>
  <div class="container">
    <div v-if="emails.length >= 10">
      <ul class="group_menu">
        <h3 style="border-bottom: 2px solid black; margin: 0; text-align: center; padding: 0.5rem;">List Mail</h3>
        <li v-for=" email  in  emails ">{{ email }}</li>
      </ul>
    </div>
    <div v-else>
      <h3 class="title_loading">Attendi qualche secondo, stiamo recuperando i dati dal server</h3>
      <div class="load">
        <div class="loading">Loading</div>
        <i class="loader fas fa-circle-notch" style="color: black;"></i>
      </div>

    </div>
  </div>
</template>

<style>
.container {
  max-width: 1020px;
  width: 70%;
  height: 100%;
  margin: auto;
  display: flex;
  align-items: center;
  justify-content: center;

  & li {
    text-align: center;
    padding: 1rem 3rem;
    list-style: none;
    border-bottom: 2px solid black;

    &:last-child {
      border-bottom-right-radius: 1.5rem;
      border-bottom-left-radius: 1.5rem;
    }

    &:hover {
      background-color: gray;
      filter: drop-shadow(0 0 10px black);
    }
  }
}

.group_menu {
  border: 2px solid black;
  border-bottom: none;
  border-radius: 1.5rem;
  padding: 0;
}

.title_loading {
  text-align: center;
}

.load {
  display: flex;
  justify-content: center;
  align-items: center;
}

.loading {
  font-size: larger;
  font-weight: 600;
  padding: 0.5rem;
}

.loader {
  font-size: 40px;
  animation: rotate 1s linear infinite;
}

@keyframes rotate {
  100% {
    transform: rotate(360deg);
  }
}
</style>
