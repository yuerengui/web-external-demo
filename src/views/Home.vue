<template>
  <div class="home">
    <span v-if="user && user.email">{{ user.email }}</span>
    <a href="https://hkdev.external.housesigma.com/apiex/auth/login" target="_blank" v-else>Login</a>
    <button @click="logout" v-if="user && user.email">logout</button>
    <br/><br/>
    <button @click="profile">get profile</button>
    <textarea name="" id="" cols="30" rows="10" v-model="test_ajax">
    </textarea>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data() {
    return {
      user: null,
      test_ajax: ''
    }
  },
  mounted() {
    this.$axios.get('https://hkdev.external.housesigma.com/apiex/profile/me').then((response) => {
      this.user = response.data.data.user
    })
  },
  methods: {
    profile() {
      this.$axios.get('https://hkdev.external.housesigma.com/apiex/profile/me').then((response) => {
        this.test_ajax = response.data.data.user
      })
    },
    logout() {
      this.$axios.get('https://hkdev.external.housesigma.com/apiex/auth/logout').then((response) => {
        console.log(response)
      })
    }
  }
}
</script>
