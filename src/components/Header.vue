<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>

export default {
  name: 'Header',
  props: {
    title: String
  },
  components: {
    
  },
  computed: {
    homePage() {
      if (this.$route.path === '/') {
        return true
      } else {
        return false
      }
    },
  },
}
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  text-align: center;
  margin-bottom: 20px;
}
</style>
