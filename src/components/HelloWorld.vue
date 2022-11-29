<template lang="pug">
  v-container
    v-row.text-center
      v-col(cols="12")
        v-img( :src="require('../assets/logo.svg')" class="my-3" contain  height="150")

      v-col.mb-4
        h3( class="display-1 font-weight-bold mb-3") 
          div Сайт тестирования 
          div нестабильных компонентов
        div(class="subheading font-weight-regular") Для начала нужно выбрать необходимый тест кейс
    .d-flex.justify-center.flex-wrap
       .mr-3.mt-2(v-for="n in 5" ) 
        router-link(to="/test/case/1")
          v-btn.white--text(:color="'#'+(Math.floor(Math.random() * 999))") тест {{n}}
    
    



</template>

<script>
  export default {
    name: 'HelloWorld',

    components:{
    },

    data(){
      return{
      }
    },
    methods:{
    }
  }
</script>
<style> 
a{
  text-decoration: none;
}
.short{
  max-width: 600px;
}
</style>