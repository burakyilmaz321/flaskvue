<template>
  <div>
    <h1>Home page</h1>
    <p>Random number is {{ randomInt }}</p>
    <button @click="getRandomInt">New random number</button>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      randomInt: 0
    }
  },
  methods: {
    getRandomInt () {
      const path = 'http://localhost:5000/api/random'
      axios.get(path)
        .then(response => {
          this.randomInt = response.data.randomNumber
        })
        .catch(error => {
          console.log(error)
        })
    }
  },
  created () {
    this.getRandomInt()
  }
}
</script>