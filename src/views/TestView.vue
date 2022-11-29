<template lang="pug">
v-container
  TestCase.pt-7.mx-auto.short(v-if="testOpen[0].start")
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
      testOpen: [{ start: false }, { start: false }, { start: false }],
    };
  },
  mounted() {
    this.testOpen[this.$route.params.num - 1].start = true;
  },
};
</script>
<style scoped>
.short {
  max-width: 600px;
}
</style>