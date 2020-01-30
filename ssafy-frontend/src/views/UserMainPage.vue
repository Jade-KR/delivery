<template>
  <div>
    <v-layout my-5>
      <UserNavBar></UserNavBar>
    </v-layout>
    <v-container fluid my-5>
      <v-row no-gutters>
        <v-col cols="6" xs="12" sm="2" md="2" lg="2">
          <!-- 검색창 -->
          <v-layout wrap>
            <v-flex>
              <v-toolbar dense>
                <v-text-field hide-details prepend-icon="search" single-line></v-text-field>
              </v-toolbar>
            </v-flex>
            <br />
            <v-flex>
              <Ranking></Ranking>
            </v-flex>
          </v-layout>
        </v-col>
        <v-col cols="12" xs="12" sm="8" lg="9" md="9">
          <v-layout pa-2>
            <Menu></Menu>
          </v-layout>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
import UserNavBar from "../components/UserNavBar";
import Ranking from "../components/Ranking";
import Menu from "../components/Menu";
export default {
  name: "UserMainPage",
  components: {
    Ranking,
    Menu,
    UserNavBar
  },
  methods: {
    test() {
      console.log(localStorage.user);
    }
  }
};
</script>

<style>
</style>