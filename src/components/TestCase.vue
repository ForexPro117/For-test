<template>
  <v-form
    ref="form"
    v-model="valid"
    lazy-validation
  >
    <v-text-field
      v-model="name"
      :counter="10"
      :rules="nameRules"
      label="Имя"
      required
    ></v-text-field>

    <v-text-field
      v-model="email"
      :rules="emailRules"
      label="E-mail"
      required
    ></v-text-field>

    <v-select
      v-model="select"
      :items="items"
      :rules="[v => !!v || 'Обязательно для заполнения']"
      label="Статус"
      required
    ></v-select>

    <v-checkbox
      v-model="checkbox"
      :rules="[v => !!v || 'Необходимо потвердить!']"
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

    <v-btn
      color="error"
      class="mr-4 mt-2"
      @click="reset"
    >
      Сбросить форму
    </v-btn>

    <v-btn
      color="warning"
      class="mt-2"
      @click="resetValidation"
    >
      Сбросить валидацию
    </v-btn>
  </v-form>
</template>
<script>
export default {
  name: "TestCase",
  data: () => ({
    valid: true,
    name: "",
    nameRules: [
      (v) => !!v || "Имя должно быть заполнено",
      (v) => (v && v.length <= 10) || "Имя должно быть менее 10 символов",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail обязателен",
      (v) => /.+@.+\..+/.test(v) || "E-mail должен быть правильным",
    ],
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