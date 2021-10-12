<template>
  <div class="menu">
    <!-- 반복문 사용법 v-for="XX in num" :ket="XX" -->
    <!-- 숫자 부분에 데이터를 넣을 수 있음 -->
    <a v-for="(a, i) in menus" :key="i">{{ a }}</a>
  </div>

  <div>
    <h4>{{ products[0] }}</h4>
    <p>50 만원</p>
    <button @click="increase">허위매물신고</button>
    <span>신고수: {{ reportNum }}</span>
    <!-- v-on:   대신 @ 사용이 가능하다 
    mouseover 등의 다른 이벤트도 다양하다-->
  </div>
  <div>
    <h4>{{ products[1] }}</h4>
    <p>60 만원</p>
  </div>
  <div>
    <h4>{{ products[2] }}</h4>
    <p>70 만원</p>
  </div>
</template>

<script>
export default {
  name: "App",
  // 데이터 바인딩. data를 변경하면 data와 관련한 HTML에도 실시간으로 반영됨. {{}} 대신 이렇게 데이터 바인딩이 되어있어야 함.
  // 고로 자주 변경되지 않는 데이터는 굳이 데이터바인딩을 하지 않아도 행복하다.
  // HTML 속성도 데이터바인딩 가능.
  // :속성="데이타이름"
  data() {
    return {
      reportNum: 0,
      menus: ["Home", "Shop", "About"],
      products: ["역삼동원룸", "천호동원룸", "마포구원룸"],
    };
  },
  // 함수 만드는 공간
  methods: {
    increase() {
      // this는 필수
      this.reportNum += 1;
    },
  },
  components: {},
};
</script>

<style>
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
