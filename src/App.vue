<template>
  <div>
    <h4>Vue3 + VeeValidate</h4>
    <Form @submit="submit" :validation-schema="schema" v-slot="{ errors }" class="form">
      <div class="form__group">
        <div class="form__col">
          <label>名字</label>
          <Field v-model="firstName" name="firstName" as="input" class="form__control" placeholder="田中" />
          <span class="form__error">{{ errors.firstName }}</span>
        </div>
        <div class="form__col">
          <label>名前</label>
          <Field v-model="lastName" name="lastName" as="input" class="form__control" placeholder="太郎" />
          <span class="form__error">{{ errors.lastName }}</span>
        </div>
        <div class="form__col">
          <label>電話番号</label>
          <Field v-model="tel" name="tel" as="input" class="form__control" placeholder="080-1234-5678" />
          <span class="form__error">{{ errors.tel }}</span>
        </div>
        <div class="form__col">
          <label>メールアドレス</label>
          <Field v-model="email" name="email" as="input" class="form__control" placeholder="example@gmail.com" />
          <span class="form__error">{{ errors.email }}</span>
        </div>
        <div class="form__col">
          <label>送信完了メールの有無</label>
          <Field name="need_email" type="radio">
            <div class="flex-box">
              <input v-model="picked" type="radio" name="need_email" value="必要"/>
              <label>必要</label>
            </div>
            <div class="flex-box">
              <input v-model="picked" type="radio" name="need_email" value="不要"/>
              <label>不要</label>
            </div>
          </Field>
        </div>
        <div class="form__col form__bind">
          <h3>入力内容</h3>
          <p>名字: {{ firstName }}</p>
          <p>名前: {{ lastName }}</p>
          <p>電話番号: {{ tel }}</p>
          <p>メールアドレス: {{ email }}</p>
          <p>送信完了メール: {{ picked }}</p>
        </div>
        <div class="form__col">
          <Field name="agree" type="checkbox" :value="false">
            <label>
              <input type="checkbox" name="agree" v-bind="field" />以上の入力内容で問題ありませんか？
            </label>
            <span class="form__error">{{ errors.agree }}</span>
          </Field>
        </div>
      </div>
      <button>送信</button>
    </Form>
  </div>
</template>

<script>
import { Field, Form } from 'vee-validate';
import * as yup from 'yup'

export default {
  data() {
    return {
      schema: yup.object().shape({
        firstName: yup.string().required(),
        lastName: yup.string().required(),
        tel: yup.number().required(),
        email: yup.string().required().email()
      }),
    }
  },
  components: {
    Form,
    Field
  }
}
</script>

<style>
label {
  display: block;
  font-size: 14px;
}

.flex-box {
  display: flex;
}

.form__bind {
  margin: 40px 0 0 0;
  font-size: 14px;
}

.form__col {
  margin-bottom: 16px;
}

.form__error {
  display: block;
  font-size: 12px;
  color: red;
}
</style>
