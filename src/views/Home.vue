<template>
  <div class="home">
    <span v-if="user && user.email">{{ user.email }}</span>
    <a href="https://hkdev.external.housesigma.com/apiex/auth/login" target="_blank" v-else>Login</a>
    <button @click="logout" v-if="user && user.email">logout</button>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {
      user: null
    }
  },
  mounted() {
    this.$axios.get('https://hkdev.external.housesigma.com/apiex/profile/me').then((response) => {
      this.user = response.data.data.user
    })
  },
  methods: {
    logout() {
      this.$axios.get('https://hkdev.external.housesigma.com/apiex/auth/logout').then((response) => {
        console.log(response)
      })
    }
  }
}
</script>
