<template>
  <v-form ref="form" v-model="valid" lazy-validation>
    <v-file-input
      show-size
      counter
      multiple
      label="Загрузите файл весом не более 5 Мб"
      :rules="fileSize"
    ></v-file-input>

    <v-text-field
      class="mt-10"
      v-model.number="lengthOtp"
      type="number"
      :rules="[(v) => !!v || 'Обязательно для заполнения']"
      label="Количество ячеек ниже"
      :min="1"
      required
    ></v-text-field>

    <v-otp-input
      v-model="otp"
      :length="lengthOtp"
      :rules="otpRule"
    ></v-otp-input>

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
  name: "TestCase3",
  data: () => ({
    valid: true,
    otp: "",
    lengthOtp: 3,
    fileSize: [
      (v) =>
        !v ||
        !v.some((file) => file.size > 3e6) ||
        "Файл не должен быть размером более 5 Мб",
    ],
    otpRule: [
        (v) => !!v || 'Обязательно для заполнения'
    ],
  }),

  computed: {
    isActive() {
      return this.otp.length === this.lengthOtp;
    },
  },

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