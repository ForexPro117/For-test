<template>
  <v-form ref="form" v-model="valid" lazy-validation>
    <vue-recaptcha sitekey="6LeIxAcTAAAAAJcZVRqyHh71UMIEGNQ_MXjiZKhI"></vue-recaptcha>

    <v-text-field
      v-model="captcha"
      :counter="10"
      :rules="nameRules"
      label="Текст"
      required
    ></v-text-field>

    <v-select
      v-model="select"
      :items="items"
      :rules="[(v) => !!v || 'Обязательно для заполнения']"
      label="Статус"
      required
    ></v-select>

    <v-checkbox
      v-model="checkbox"
      :rules="[(v) => !!v || 'Необходимо потвердить!']"
      label="Вы уверены?"
      required
    ></v-checkbox>

    <v-btn
      :disabled="!valid"
      color="success"
      class="mr-4 mt-2"
      @click="validate"
    >
      Проверить
    </v-btn>

    <v-btn color="error" class="mr-4 mt-2" @click="reset">
      Сбросить форму
    </v-btn>

    <v-btn color="warning" class="mt-2" @click="resetValidation">
      Сбросить валидацию
    </v-btn>
  </v-form>
</template>
<script>
import { VueRecaptcha } from "vue-recaptcha";
export default {
  components: {
    VueRecaptcha,
  },
  name: "TestCase",
  data: () => ({
    sitekey: "",
    valid: true,
    select: null,
    items: ["Тут", "Я", "", "Или нет"],
    checkbox: false,
  }),

  methods: {
    validate() {
      this.$refs.form.validate();
    },
    reset() {
      this.$refs.form.reset();
    },
    resetValidation() {
      this.$refs.form.resetValidation();
    },
  },
};
</script>