<template>
  <div>
    <v-btn icon @click.stop="dialog = true">
      <v-icon>
        mdi-account
      </v-icon>
    </v-btn>
    <v-dialog
      v-model="dialog"
      max-width="380"
    >
      <v-card>
        <v-card-title class="headline mb-5">
          로그인
          <v-spacer />
          <v-btn
            icon
            @click.stop="dialog = false"
          >
            <v-icon>
              mdi-close
            </v-icon>
          </v-btn>
        </v-card-title>

        <v-card-text>
          <v-form>
            <v-text-field
              name="email"
              type="email"
              placeholder="이메일을 입력하세요."
              outlined
              hide-details
              class="mb-3"
            />

            <v-text-field
              name="password"
              type="password"
              placeholder="비밀번호를 입력하세요."
              outlined
              hide-details
              class="mb-3"
            />
            <v-btn
              type="submit"
              color="primary"
              block
              x-large
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
      dialog: true
    }
  },
  methods: {

  }
}
</script>
