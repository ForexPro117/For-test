<template lang="pug">
v-container
  TestCase.pt-7.mx-auto.short(v-if="testOpen == 1" @result="viewResult")
  TestCase2.pt-7.mx-auto.short(v-if="testOpen == 2" @result="viewResult")
  TestCase3.pt-7.mx-auto.short(v-if="testOpen == 3" @result="viewResult")
  v-input {{result}} 
</template>

<script>
import TestCase from "../components/TestCase"
import TestCase2 from "../components/TestCase2.vue"
import TestCase3 from "../components/TestCase3.vue";
export default {
  name: "TestView",
  components: {
    TestCase,
    TestCase2,
    TestCase3,
  },
  data() {
    return {
      testOpen: 1,
      result:{}
    };
  },
  mounted() {
    this.testOpen = this.$route.params.num;
  },
  methods:{
    viewResult(val){
      this.result = val
    }
  }
};
</script>
<style scoped>
.short {
  max-width: 600px;
}
</style>