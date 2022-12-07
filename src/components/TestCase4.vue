<template>
  <v-form ref="form" v-model="valid" lazy-validation>
    <v-text-field :counter="10" v-model="text"
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
    <v-text-field class="ml-10" style="max-width:200px" v-model="code"
    :rules="[(v) => (!!v && (v === 'hne' || v.length > 10)) || 'Неверный код!']" label="Код" placeholder="Placeholder" outlined></v-text-field>
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
    text:"",
    code:""
  }),

  created() {
  },
  methods: {
    validate() {
      this.$refs.form.validate()
      this.$emit("result",{
        Текст:this.text,
        Статус:this.select,
        'Вы уверены?':this.checkbox? 'да':'нет',
        Код:this.code
        })
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
