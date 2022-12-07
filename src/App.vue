<template lang="pug">
v-app
  v-app-bar(app, color="primary", dark, rounded)
      router-link(v-if="visible", to="/") 
        v-btn(icon, @click="visible = false")
          v-icon mdi-arrow-left
      
      v-toolbar-title.mx-auto Даешь сервелаты в массы!
  v-main
      router-view()
</template>

<script>
export default {
  name: 'App',

  data() {
    return {
      visible: false,
      arr: false,
    }
  },
  methods: {
    update() {
      this.visible = true
    },
  },
  watch: {
    $route() {
      console.log(this.$route.name)
      this.visible = this.$route.name === 'home' ? false : true
    },
  },
}
</script>
<style scoped>
.logo {
  font-family: 'Roboto';
  font-size: 20px;
}
</style>
