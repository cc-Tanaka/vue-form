<template>
  <div>
    <h4>Vue3 + VeeValidate</h4>
    <Form v-slot="{ errors }" class="form">
      <div class="form__group">
        <div class="form__col">
          <label>名字</label>
          <Field name="firstName" type="text" class="form__contro;" placeholder="田中" rules="required" />
          <span class="form__error">{{ errors.firstName }}</span>
        </div>
        <div class="form__col">
          <label>名前</label>
          <Field name="lastName" type="text" class="form__contro;" placeholder="太郎" rules="required" />
          <span class="form__error">{{ errors.lastName }}</span>
        </div>
        <div class="form__col">
          <label>電話番号</label>
          <Field name="tel" type="text" class="form__contro;" placeholder="080-1234-5678" rules="required" />
          <span class="form__error">{{ errors.tel }}</span>
        </div>
        <div class="form__col">
          <label>メールアドレス</label>
          <Field name="mail" type="text" class="form__contro;" placeholder="example@gmail.com" rules="required" />
          <span class="form__error">{{ errors.mail }}</span>
        </div>
      </div>
      <button type="submit">送信</button>
    </Form>
  </div>
</template>

<script>
import { Field, Form } from 'vee-validate';
import { defineRule } from 'vee-validate';
import { required } from '@vee-validate/rules';

defineRule('required', required);

export default {
  data() {
    return {
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

.form__col {
  margin-bottom: 16px;
}

.form__error {
  display: block;
  font-size: 12px;
  color: red;
}
</style>
