<template lang="pug">
  v-app
    v-app-bar(app  color="primary" dark)  
      .mx-auto.logo Даёшь сервелаты в массы!
    v-main
      router-view
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  }),
};
</script>
<style scoped>
.logo{
  font-family: 'Roboto';
  font-size: 20px;
}
</style>