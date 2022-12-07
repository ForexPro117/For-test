<template>
  <v-form ref="form" v-model="valid" lazy-validation>
    <v-text-field :counter="10"
    :rules="[(v) => (v && v.length < 15) || 'Поле должно быть не более 10 симвоов']" label="Текст" required></v-text-field>

    <v-select
      v-model="select"
      :items="items"
      :rules="[(v) => !!v || 'Обязательно для заполнения',
      ]"
      label="Статус"
      required
    ></v-select>

    <v-checkbox
      v-model="checkbox"
      :rules="[(v) => !!v || 'Необходимо потвердить!']"
      label="Вы уверены?"
      required
    ></v-checkbox>
    <div class="d-flex">
      <v-img
      max-height="50"
      max-width="130"
      src="https://vk.com/captcha.php?sid=115072837620&s=1"
    ></v-img>
    <v-text-field class="ml-10" style="max-width:200px"
    :rules="[(v) => (!!v && v === 'pidor') || 'Неверный код!']" label="Код" placeholder="Placeholder" outlined></v-text-field>
    </div>
    
    <v-btn :disabled="!valid" color="success" class="mr-4 mt-2" @click="validate">
      Проверить
    </v-btn>

    <v-btn color="error" class="mr-4 mt-2" @click="reset"> Сбросить форму </v-btn>

    <v-btn color="warning" class="mt-2" @click="resetValidation">
      Сбросить валидацию
    </v-btn>
  </v-form>
</template>
<script>
export default {
  components: {},
  name: 'TestCase',
  data: () => ({
    sitekey: '',
    valid: true,
    select: null,
    items: ['1', '2', '3', '4'],
    checkbox: false,
    nameRules: '',
  }),

  created() {
  },
  methods: {
    validate() {
      this.$refs.form.validate()
    },
    reset() {
      this.$refs.form.reset()
    },
    resetValidation() {
      this.$refs.form.resetValidation()
    },
  },
}
</script>
