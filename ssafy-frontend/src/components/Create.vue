<template>
  <div v-if="userName !== writer">
    <p>올바른 접근 방식이 아닙니다.</p>
    <v-btn small color="primary" @click="move()">글목록</v-btn>
  </div>
  <div v-else-if="index !==undefined">
    <input v-model="category" placeholder="category" />
    <input v-model="title" placeholder="title" />
    <input v-model="body" placeholder="body" />
    <v-btn
      small
      color="error"
      @click="index !== undefined? updated() : write()"
    >{{index !== undefined ? '수정': '작성'}}</v-btn>
    <v-btn small color="primary" @click="move()">글목록</v-btn>
  </div>
  <div v-else>
    <select v-model="category">
      <option disabled value>Please select one</option>
      <option>치킨</option>
      <option>피자</option>
      <option>족발</option>
    </select>
    <input v-model="address" placeholder="address" />
    <input v-model="title" placeholder="title" />
    <input v-model="body" placeholder="body" />
    <v-btn
      small
      color="error"
      @click="index !== undefined? updated() : write()"
    >{{index !== undefined ? '수정': '작성'}}</v-btn>
    <v-btn small color="primary" @click="move()">글목록</v-btn>
  </div>
</template>

<script>
import axios from "axios";
import test from "../services/test";
import Read from "./Read";
export default {
  name: "Create",
  mounted() {
    this.get_info();
  },

  data() {
    const index = this.$route.params.contentId;
    console.log(index);
    return {
      userName: localStorage.userName,
      board: [],
      num: "",
      index: index,
      category: "",
      address: "",
      writer: "",
      title: "",
      body: ""
    };
  },
  methods: {
    move() {
      this.$router.push({
        name: "Read"
      });
    },
    write() {
      axios({
        method: "post",
        url: "http://192.168.100.92:8080/notice/board",
        data: {
          category: this.category,
          address: this.address,
          title: this.title,
          body: this.body,
          writer: localStorage.userName
        }
      }).then(() => {
        this.$router.push({ name: "Read" });
      });
    },
    updated() {
      axios({
        method: "put",
        url: "http://192.168.100.92:8080/notice/board",
        data: {
          num: this.num,
          category: this.category,
          address: this.address,
          title: this.title,
          body: this.body,
          writer: this.writer
        }
      }).then(() => {
        this.$router.push({ name: "Read" });
      });
    },
    get_info() {
      test.backendService(
        res => {
          this.board = res;

          console.log(this.index);
          if (typeof this.index !== "undefined") {
            this.num = this.board[this.index].num;
            this.category = this.board[this.index].category;
            this.address = this.board[this.index].address;
            this.writer = this.board[this.index].writer;
            this.title = this.board[this.index].title;
            this.body = this.board[this.index].body;
          }
          console.log(this.board);
        },
        error => {}
      );
    }
  }
};
</script>

<style>
</style>