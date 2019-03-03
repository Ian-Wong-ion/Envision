<template>
<v-card>
  <v-form>
    <v-text-field
        v-model="name"
        :rules="nameRules"
        label="姓名"
        required
    ></v-text-field>

    <v-text-field
        v-model="email"
        :rules="emailRules"
        label="现用邮箱"
        required
    ></v-text-field>
    <v-text-field
        v-model="Password"
        :append-icon="show1 ? 'visibility_off' : 'visibility'"
        :rules="[PasswordRules.required, PasswordRules.min]"
        :type="show1 ?  'Password': 'text'"
        name="input-10-1"
        label="密码"
        hint="密码长度必须大于 6 个字符"
        counter
        @click:append="show1 = !show1"
    ></v-text-field>
    <v-text-field
        v-model="newEmail"
        :rules="newEmailRules"
        label="新的邮箱"
        required
    ></v-text-field>
     <v-checkbox
      v-model="checkbox"
      :rules="[v => !!v || '您必须同意才可以进行提交！']"
      label="是否确认无误并同意因问发送验证邮件至您已绑定的邮箱?"
      required
    ></v-checkbox>
    <v-btn
      color="success"
      @click="submit"
    >
      提交
    </v-btn>

    <v-btn
      color="error"
      @click="reset"
    >
      取消
    </v-btn>
  </v-form>
</v-card>
</template>

<script>
  export default {
    data () {
      return {
        checkbox: false,
        show1: true,
        name: '',
        nameRules: [
            v => !!v || '这是一个必填项目',

        ],
        email: '',
        emailRules: [
            v => !!v || '这是一个必填项目',
            v => /.+@.+/.test(v) || '邮箱格式不正确'
        ],
        newEmail: '',
        newEmailRules: [
            v => !!v || '这是一个必填项目',
            v => /.+@.+/.test(v) || '邮箱格式不正确'
        ],
        Password: '',
        PasswordRules: {
          required: value => !!value || '这是一个必填项目',
          min: v => v.length >= 6 || '密码长度必须大于 6 个字符',
        },
    
      }
    },
    methods: {
      submit () {
        this.$v.$touch()
      },
      reset () {
        this.$refs.form.reset()
      },
    }
  }
</script>