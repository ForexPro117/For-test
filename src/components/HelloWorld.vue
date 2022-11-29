<template lang="pug">
v-container
  v-row.text-center
    v-col(cols="12")
      v-img.my-3(:src="require('../assets/logo.svg')", contain, height="150")

    v-col.mb-4
      h3.display-1.font-weight-bold.mb-3 
        div Сайт тестирования
        div нестабильных компонентов
      .subheading.font-weight-regular Для начала нужно выбрать необходимый тест кейс
  .d-flex.justify-center.flex-wrap
    .mr-3.mt-2(v-for="n in 5") 
      router-link(:to="'/test/case/' + n")
        v-btn.white--text.text(@click="$emit('switch')" :color="'#' + Math.floor(Math.random() * 999)") тест {{ n }}
</template>

<script>
export default {
  name: "HelloWorld",

  components: {},

  data() {
    return {};
  },
  methods: {
  },
};
</script>
<style>
a {
  text-decoration: none;
}
.text {
  text-shadow: 1px 0 1px rgba(0, 0, 0, 0.171), 0 1px 1px rgba(0, 0, 0, 0.233),
    -1px 0 1px rgba(0, 0, 0, 0.219), 0 -1px 1px rgba(0, 0, 0, 0.178);
}
</style>