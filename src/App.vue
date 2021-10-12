<template>
  <div class="black-bg" v-if="modalState === true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
      <button @click="modalState = false">닫기</button>
    </div>
  </div>

  <div class="menu">
    <!-- 반복문 사용법 v-for="XX in num" :ket="XX" -->
    <!-- 숫자 부분에 데이터를 넣을 수 있음 -->
    <a v-for="(a, i) in menus" :key="i">{{ a }}</a>
  </div>

  <!-- <div v-for="(a, i) in products" :key="i">
    <h4>{{ a }}</h4>
    <p>{{ price[i] }} 만원</p>
    <button @click="increase(i)">허위매물신고</button>
    <span>신고수: {{ reportNum[i] }}</span>
    v-on:   대신 @ 사용이 가능하다 
    mouseover 등의 다른 이벤트도 다양하다-->
  <!-- </div> -->
  <div v-for="(a, i) in onerooms" :key="i">
    <img :src="onerooms[i].image" class="room-img" />
    <h4>{{ onerooms[i].title }}</h4>
    <p>{{ onerooms[i].price }}</p>
  </div>
</template>

<script>
import onerooms from "./onerooms";

export default {
  name: "App",
  // 데이터 바인딩. data를 변경하면 data와 관련한 HTML에도 실시간으로 반영됨. {{}} 대신 이렇게 데이터 바인딩이 되어있어야 함.
  // 고로 자주 변경되지 않는 데이터는 굳이 데이터바인딩을 하지 않아도 행복하다.
  // HTML 속성도 데이터바인딩 가능.
  // :속성="데이타이름"

  // Vue를 개발할떄는 데이터를 어떻게 할지 생각하며 만드는 것이 좋다.
  data() {
    return {
      onerooms: onerooms,
      modalState: false,
      menus: ["Home", "Shop", "About"],
    };
  },
  // 함수 만드는 공간
  methods: {
    increase(num) {
      // this는 필수
      this.reportNum[num] += 1;
    },
  },
  components: {},
};
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed;
  padding: 20px;
}
.white-bg {
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img {
  width: 50%;
  margin-top: 40px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}
</style>
