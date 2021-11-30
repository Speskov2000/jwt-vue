<template>
  <div class="home">
    <h1>Home</h1>
    <p v-if="user_data != '' "> {{user_data}} </p>
    <p v-else>Вы не авторизованы!</p>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'Home',
  data() {
    return {
      user_data: ''
    }
  },

  mounted() {
    this.getMe()
  },
  methods: {
    getMe(e) {
      axios
        .get("/auth/users/me")
        .then(response => {
          console.log(response)
          this.user_data = response.data.username
        })
        .catch(error => {
          console.log(error)
        })
    }
  }
}
</script>
