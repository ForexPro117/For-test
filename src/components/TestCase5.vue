<template>
  <v-form ref="form" v-model="valid" lazy-validation>

    <v-text-field
    v-model="firstName"
    label="Фамилия"
    ></v-text-field>

    <v-text-field
    v-model="secondName"
    label="Имя"
    ></v-text-field>

    <v-text-field
    v-model="thirdName"
    label="Отчество"
    ></v-text-field>

    <v-menu
      ref="menu"
      v-model="menu"
      :close-on-content-click="false"
      transition="scale-transition"
      offset-y
      min-width="auto"
      :rules="[[(v) => !!v || 'Обязательно для заполнения']]"
    >
      <template v-slot:activator="{ on, attrs }">
        <v-text-field
          v-model="date"
          label="Дата рождения"
          prepend-icon="mdi-calendar"
          readonly
          v-bind="attrs"
          v-on="on"
        ></v-text-field>
      </template>
      <v-date-picker
        v-model="date"
        :active-picker.sync="activePicker"
        :max="
          new Date(Date.now() - new Date().getTimezoneOffset() * 60000)
            .toISOString()
            .substr(0, 10)
        "
        min="1900-01-01"
        @change="save"
      ></v-date-picker>
    </v-menu>

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
export default {
  name: "TestCase5",
  data: () => ({
    valid: true,
    date: null,
    menu: false,
    firstName: '',
    secondName: '',
    thirdName: '',
  }),

  methods: {
    save(date) {
      this.$refs.menu.save(date);
    },
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