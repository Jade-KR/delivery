<template>
  <div>
    <v-toolbar width="100%" absolute dense style="position:fixed;">
      <v-app-bar-nav-icon @click.stop="overlay = !overlay"></v-app-bar-nav-icon>
      <v-toolbar-title>
        <v-label>
          <router-link to="/StoreMainPage" tag="span" style="cursor: pointer">
            <v-img src="../assets/홈3.png" width="300" text aspect-ratio="7.0"></v-img>
          </router-link>
        </v-label>
      </v-toolbar-title>
      <v-spacer>
        <v-text class="font-weight-bold">사장님 공간</v-text>
      </v-spacer>
      <v-toolbar-items class="hidden-xs-only">
        <v-btn text v-for="item in menuItems" :key="item.title" :to="item.path">
          <v-icon left dark>{{ item.icon }}</v-icon>
          {{ item.title }}
        </v-btn>
      </v-toolbar-items>
    </v-toolbar>

    <!-- 메뉴 아이콘 클릭 -->
    <v-overlay :value="overlay">
      <v-navigation-drawer v-model="overlay" absolute color="transparent" style="position:fixed;">
        <v-layout>
          <v-flex>
            <v-toolbar width="100%" absolute dense color="transparent" style="position:fixed;">
              <v-icon @click.stop="overlay = !overlay" style="cursor:pointer;">mdi-reply</v-icon>

              <!-- mdi-arrow-left, mdi-reply -->
            </v-toolbar>
          </v-flex>
          <v-flex absolute fill-height>
            <v-card fluid color="transparent">
              <br />
              <br />

              <v-list nav>
                <v-list-item-group>
                  <v-list-item v-for="item in menuItems" :key="item.title" :to="item.path">
                    <v-tooltip bottom>
                      <template v-slot:activator="{ on }">
                        <v-list-item-content v-on="on">
                          <v-list-item-title>
                            <span
                              class="display-1 text-shadow font-weight-bold text-center"
                            >{{ item.title }}</span>
                          </v-list-item-title>
                        </v-list-item-content>
                      </template>
                      <span>{{item.info}}</span>
                    </v-tooltip>
                  </v-list-item>
                </v-list-item-group>
              </v-list>
            </v-card>
          </v-flex>
        </v-layout>
      </v-navigation-drawer>
    </v-overlay>

    <v-navigation-drawer v-model="sidebar" temporary style="position:fixed;">
      <v-list nav dense>
        <v-list-item-group>
          <v-list-item v-for="item in menuItems" :key="item.title" :to="item.path">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>

            <v-list-item-content>
              <v-list-item-title>{{ item.title }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
  </div>
</template>
 
<script>
export default {
  name: "main-header",
  data() {
    return {
      appTitle: "'반반한 동네' 사장님 공간",
      sidebar: false,
      overlay: false,
      menuItems: [
        {
          title: "게시판",
          path: "/read",
          icon: "account_circle",
          info: "게시판 가고싶으면 클릭!!"
        },
        {
          title: "내 정보",
          path: "/read",
          icon: "folder_open",
          info: "내 정보 가고싶으면 클릭!!"
        },
        {
          title: "고객 센터",
          path: "/",
          icon: "folder_open",
          info: "고객 센터 가고싶으면 클릭!!"
        },
        {
          title: "로그아웃",
          path: "/",
          icon: "folder_open",
          info: "로그아웃 하고싶으면 클릭!!"
        }
      ]
    };
  }
};
</script>
 
<style>
</style>
