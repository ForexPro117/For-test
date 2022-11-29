<template lang="pug">
v-container
  TestCase.pt-7.mx-auto.short(v-if="testOpen == 1")
</template>

<script>
import TestCase from "../components/TestCase";
export default {
  name: "TestView",
  components: {
    TestCase,
  },
  data() {
    return {
      testOpen: 1
    };
  },
  mounted() {
    this.testOpen = this.$route.params.num;
  },
};
</script>
<style scoped>
.short {
  max-width: 600px;
}
</style>