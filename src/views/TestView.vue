<template lang="pug">
  v-container
    h1.ml-10 ТестирОвочка
    TestCase.pt-7.mx-auto.short(v-if="testOpen[0].start")
</template>
<script>
import TestCase from '../components/TestCase'
export default {
  name: 'TestView',
    components:{
      TestCase
    },
   data(){
      return{
        items: ["arr","addd" ],
        testOpen: [{start:false},{start:false},{start:false}],
      }
    },
    mounted(){
      this.testOpen[this.$route.params.num-1].start=true
    }
}
</script>