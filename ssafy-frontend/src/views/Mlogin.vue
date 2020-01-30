<template >
  <v-content relative>
    <v-container class="fill-height" fluid>
      <v-row justify="center">
        <v-col cols="12" sm="8" md="3">
          <v-card-text class="vcard" text-xs-center>
            <v-form @submit.prevent="login">
              <p class="display-1 text-center font-weight-bold">반반한 동네</p>
              <br />
              <v-row>
                <v-text-field
                  v-model="id"
                  id="id"
                  :rules="idRules"
                  :counter="10"
                  height="3em"
                  label="아이디"
                  type="text"
                  outlined
                  dense
                  required
                ></v-text-field>
              </v-row>
              <v-row>
                <v-text-field
                  v-model="pw"
                  id="pw"
                  height="3em"
                  label="비밀번호"
                  outlined
                  dense
                  type="password"
                  @keyup.enter="Mlogin()"
                ></v-text-field>
              </v-row>
              <v-row fluid>
                <a>아이디</a>/
                <a>비밀번호 찾기</a>
                <router-link :to="{ name: 'MsignUp'}" style="margin-left: 20px;">회원가입</router-link>
                <router-link :to="{ path: '/'}" style="margin-left: 230px;">메인페이지</router-link>
              </v-row>
              <br />
              <v-row>
                <v-btn
                  large
                  color="primary"
                  @click="Mlogin()"
                  width="100%"
                  height="50"
                  fill="#0076ff"
                  font-size="16"
                  font-family="SourceHanSansK-Bold, Source Han Sans K"
                  font-weight="700"
                >로그인</v-btn>
              </v-row>
              <br />
              <v-row justify="center">
                <td>SNS 로그인</td>
              </v-row>
              <br />
              <v-row justify="center">
                <div class="social">
                  <KakaoLogin></KakaoLogin>
                </div>
                <div>
                  <GoogleLogin></GoogleLogin>
                </div>
              </v-row>
            </v-form>
          </v-card-text>
        </v-col>
      </v-row>
    </v-container>
  </v-content>
</template>

<script>
import Kakao from "../../Kakao.js";
import KakaoLogin from "@/components/KakaoLogin.vue";
import GoogleLogin from "@/components/GoogleLogin.vue";

export default {
  components: {
    KakaoLogin,
    GoogleLogin
  },
  data() {
    return {
      id: "",
      pw: "",
      name: 123,
      tel: 123,
      email: 123,
      address: 123,
      chk: 0,
      point: 0,
      signupDate: 214
    };
  },
  methods: {
    Mlogin() {
      this.$store
        .dispatch("Mlogin", {
          id: this.id,
          pw: this.pw,
          name: this.name,
          tel: this.tel,
          email: this.email,
          address: this.address,
          chk: this.chk,
          point: this.point,
          signupDate: this.signupDate
        })
        .then(() => {
          this.$router.push({ name: "UserMainPage" });
        })
        .catch(err => {
          console.log(err.response);
        });
    }
  }
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Nanum+Gothic&display=swap");
@import url("https://fonts.googleapis.com/css?family=Black+Han+Sans|Do+Hyeon|Jua|Nanum+Gothic|Sunflower:300");
* {
  font-family: "Do Hyeon", sans-serif;
}
.social {
  margin-right: 20px;
}
</style>