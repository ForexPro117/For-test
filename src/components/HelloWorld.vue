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
    .d-flex.flex-row-reverse.justify-center.flex-wrap
       .mr-3.mt-2(v-for="i,index in testOpen" ) 
          v-btn.white--text(:color="'#'+(Math.floor(Math.random() * 999))" @click="i.start=!i.start") тест {{index+1}}
    
    TestCase.pt-7.mx-auto.short(v-if="!testOpen[0].start")



</template>

<script>
import TestCase from '../components/TestCase'
  export default {
    name: 'HelloWorld',

    components:{
      TestCase
    },

    data(){
      return{
        items: ["arr","addd" ],
        testOpen: [{start:false},{start:false},{start:false}],
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