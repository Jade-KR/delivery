<template>
  <div>
    <h1>Detail</h1>
    <ul>
      <li :key="index" v-for="(value,index) in board" v-if="value.num == contentId">
        <h2>제목: {{value.title}}</h2>
        <p>글번호: {{value.num}}</p>
        <p>메뉴: {{value.category}}</p>
        <p>주소: {{value.address}}</p>

        <p>내용: {{value.body}}</p>
        <p>글쓴이 id: {{value.writer}}</p>

        <v-btn
          v-if="userName === value.writer"
          small
          color="error"
          @click="deleteTest(value.num)"
        >글삭제</v-btn>
        <v-btn v-if="userName === value.writer" small color="danger" @click="updateData(index)">글수정</v-btn>
        <v-btn small color="primary" @click="move()">글목록</v-btn>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";
import test from "../services/test";
export default {
  name: "Detail",
  mounted() {
    this.get_info();
    console.log(localStorage.userName);
  },
  props: ["contentId"],
  data() {
    return {
      board: [],
      userName: localStorage.userName
    };
  },
  methods: {
    get_info(func) {
      test.backendService(
        res => {
          this.board = res;
        },
        error => {}
      );
    },
    move() {
      this.$router.push({
        name: "Read"
      });
    },
    deleteTest(num) {
      axios({
        method: "Delete",
        url: `http://192.168.100.92:8080/api/board/${num}`
      }).then(res => this.move());
    },
    updateData(num) {
      this.$router.push({
        path: `../Create/${num}`
      });
    }
  }
};
</script>
