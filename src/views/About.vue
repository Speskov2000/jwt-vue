<template>
  <div class="about">
    <h1>This is an about page</h1>
    <p v-if="aboutText!='' "> {{aboutText}} </p>
    <p v-else>Вы не авторизованы!</p>
    
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'About',
  data() {
    return {
      aboutText: '',
    }
  },
  mounted() {
    this.getText()
  },
  methods: {
    getText(e) {
      axios
      .get('/about')
      .then(response => {
        console.log(response)
        this.aboutText = response.data.key
      })
    }
  }
}
</script>
