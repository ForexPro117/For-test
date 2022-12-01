<template>
    <v-form ref="form" v-model="valid" lazy-validation>
      <v-text-field
        v-model="phone"
        :counter="11"
        :rules="phoneRules"
        placeholder="89991234567"
        label="Номер телефона"
        required
      ></v-text-field>
  
      <v-switch
        v-model="switch1"
        inset
        label="Тыкни на меня"
      ></v-switch>
  
      <v-text-field
        :disabled="!switch1"
        v-model="text"
        :rules="textRules"
        label="Просто текст"
        required
      ></v-text-field>
  
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
  export default {
    name: "TestCase2",
    data: () => ({
      valid: true,
      phone: "",
      phoneRules: [
        (v) => !!v || "Номер телефона должен быть заполнен",
        (v) => (v && v.length == 11) || "Номер телефона должен быть состоять из ровно 11 цифр",
        (v) => /8[0-9]{10}/.test(v) || "Номер телефона должен быть правильным"
      ],
      textRules: [
        (v) => !!v || "Текст должен быть заполнен",
      ],
      switch1: false,
      select: null,
      items: ["Тут", "Я", "", "Или нет"],
      checkbox: false,
    }),
  
    methods: {
      validate() {
        this.$refs.form.validate();
        this.getResult()
      },
      reset() {
        this.$refs.form.reset();
      },
      resetValidation() {
        this.$refs.form.resetValidation();
      },
      getResult(){
        this.$emit("result",{phone:this.phone})
      },
    },
  };
  </script>