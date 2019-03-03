<template>
<v-card>
  <v-form>
    <v-text-field
        :error-messages="nameErrors"
        v-model="name"
        required
        label="请输入你的真实姓名"
        @input="$v.name.$touch()"
        @blur="$v.name.$touch()"
    ></v-text-field>

    <v-text-field
        v-model="email"
        label="邮箱"
        required
        :error-messages="emailErrors"
        @input="$v.email.$touch()"
        @blur="$v.email.$touch()"
    ></v-text-field>
    <v-text-field
        v-model="oldPassword"
        :append-icon="show1 ? 'visibility_off' : 'visibility'"
        :error-messages="oldPasswordErrors"
        required
        @input="$v.oldPassword.$touch()"
        @blur="$v.oldPassword.$touch()"
        :type="show1 ?  'Password': 'text'"
        name="input-10-1"
        label="旧密码"
        hint="密码长度必须大于 6 个字符"
        counter
        @click:append="show1 = !show1"
    ></v-text-field>
    <v-text-field
        v-model="password"
        :append-icon="show2 ? 'visibility_off' : 'visibility'"
        :error-messages="passwordErrors"
      
        @input="$v.password.$touch()"
        @blur="$v.password.$touch()"
        :type="show2 ? 'Password': 'text'"
        name="input-10-1"
        label="新密码"
        hint="密码长度必须大于 6 个字符"
        counter
        @click:append="show2 = !show2"
    ></v-text-field>
    <v-text-field
        v-model="confirmPassword"
        :append-icon="show3 ? 'visibility_off' : 'visibility'"
        :error-messages="repeatPasswordErrors"
        required
        @input="$v.confirmPassword.$touch()"
        @blur="$v.confirmPassword.$touch()"
        :type="show3 ? 'Password': 'text'"
        name="input-10-1"
        label="确认新密码"
        hint="密码长度必须大于 6 个字符"
        counter
         @click:append="show3 = !show3"
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

import { required, sameAs, minLength, email, maxLength } from 'vuelidate/lib/validators'



  export default {
    data () {
      return {
        checkbox: false,
        show1: true,
        show2: true,
        show3: true,
        name: '',
        email: '',
        oldPassword: '',
        password: '',
        confirmPassword:'',
      }
    },
    validations: {
        name: {
            required,
            maxLength: maxLength(10)
        },
        email: {
            required,
            email
        },
        oldPassword: {
            required,
            minLength: minLength(6)
        },
        password: {
            required,
            minLength: minLength(6)
        },
        confirmPassword: {
            required,
            sameAsPassword: sameAs('password')
        },
    },
    computed: {
        nameErrors () {
            const errors = [];
            if (!this.$v.name.$dirty) return errors;
            !this.$v.name.maxLength && errors.push('姓名不能超过 10 汉字或字符');
            !this.$v.name.required && errors.push('这是一个必填项目');
            return errors;
        },
        emailErrors () {
            const errors = [];
            if (!this.$v.email.$dirty) return errors;
            !this.$v.email.email && errors.push('邮箱格式不正确');
            !this.$v.email.required && errors.push('这是一个必填项目');
            return errors;
        },
        oldPasswordErrors () {
            const errors = [];
            if (!this.$v.oldPassword.$dirty) return errors;
            !this.$v.oldPassword.minLength && errors.push('密码长度必须大于 6 个字符');
            !this.$v.oldPassword.required && errors.push('这是一个必填项目');
            return errors;
        },
        passwordErrors () {
            const errors = [];
            if (!this.$v.password.$dirty) return errors;
            !this.$v.password.minLength && errors.push('密码长度必须大于 6 个字符');
            !this.$v.password.required && errors.push('这是一个必填项目');
            return errors;
        },
        repeatPasswordErrors () {
            const errors = [];
            if (!this.$v.confirmPassword.$dirty) return errors;
            !this.$v.confirmPassword.sameAsPassword && errors.push('前后两次输入的密码不一致');
            !this.$v.confirmPassword.required && errors.push('这是一个必填项目');
            return errors;
        },
    }
        
}
 
</script>