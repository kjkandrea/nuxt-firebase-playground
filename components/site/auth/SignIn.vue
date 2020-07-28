<template>
  <div>
    <v-btn icon @click.stop="onOpenDialog">
      <v-icon>
        mdi-account
      </v-icon>
    </v-btn>
    <v-dialog
      v-model="dialog"
      persistent
      max-width="380"
    >
      <v-card>
        <v-card-title class="headline mb-5">
          로그인
          <v-spacer />
          <v-btn
            icon
            @click.stop="onCloseDialog"
          >
            <v-icon>
              mdi-close
            </v-icon>
          </v-btn>
        </v-card-title>

        <v-card-text>
          <v-form
            ref="form"
            v-model="valid"
            @submit.prevent="onSubmitForm"
          >
            <v-text-field
              ref="focusInput"
              v-model="email"
              name="email"
              type="email"
              placeholder="이메일을 입력하세요."
              outlined
              :rules="emailRules"
            />

            <v-text-field
              v-model="password"
              name="password"
              type="password"
              placeholder="비밀번호를 입력하세요."
              outlined
              :rules="passwordRules"
            />
            <v-btn
              type="submit"
              color="primary"
              block
              x-large
              :disabled="!valid"
            >
              로그인 하기
            </v-btn>
          </v-form>
        </v-card-text>

        <v-card-actions class="other-auth flex-column">
          <p>또는 다음의 방식으로 이용 가능 합니다.</p>
          <v-btn
            block
            rounded
            outlined
            large
          >
            <v-icon class="mr-2">mdi-google</v-icon>
            Google 계정으로 이용하기
          </v-btn>
          <v-btn
            block
            rounded
            outlined
            large
          >
            <v-icon class="mr-2">mdi-facebook</v-icon>
            Facebook 계정으로 이용하기
          </v-btn>
          <v-btn
            block
            rounded
            outlined
            large
          >
            <v-icon class="mr-2">mdi-github</v-icon>
            Github 계정으로 이용하기
          </v-btn>
          <v-btn
            block
            rounded
            outlined
            large
          >
            <v-icon class="mr-2">mdi-apple</v-icon>
            Apple 계정으로 이용하기
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data () {
    return {
      dialog: false,
      valid: false,
      email: '',
      password: '',
      emailRules: [
        v => !!v || '이메일은 필수입니다.',
        v => /.+@.+/.test(v) || '이메일이 유효하지 않습니다.'
      ],
      passwordRules: [
        v => !!v || '비밀번호는 필수입니다.'
      ]
    }
  },
  methods: {
    onSubmitForm () {
      if (this.$refs.form.validate()) {
        alert('로그인을 시도함')
      }
    },
    onOpenDialog () {
      this.dialog = true
      setTimeout(_ =>
        this.$refs.focusInput.focus()
      , 300)
    },
    onCloseDialog () {
      this.dialog = false
      this.valid = false
      this.email = ''
      this.password = ''
    }
  }
}
</script>
