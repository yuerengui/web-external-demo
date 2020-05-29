<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
  </div>
</template>

<script>

export default {
  name: 'Home',
  created() {
    this.$axios.get('https://hkdev.external.housesigma.com/apiex/index').then((response) => {
      console.log(response)
    })
  }
}
</script>
