<template>
  <div id="app">

    <!-- 모달창 -->
    <Modal :원룸들="원룸들" :idx="idx" :visibleModal="visibleModal" />
    <!-- // 모달창 -->

    <!-- 메뉴 -->
    <div class="menu">
      <a v-for="menuList in 메뉴들" :key="menuList">{{ menuList }}</a>
    </div>
    <!-- // 메뉴 -->

    <!-- 홍보용 -->
    <Discount v-bind="obj" :이름="obj.name" :나이="obj.age" />
    <!-- // 홍보용 -->

    <!-- 카드 -->
    <Card :oneroom="원룸들[0]" />
    <Card :oneroom="원룸들[1]" />
    <Card :oneroom="원룸들[2]" />
    <Card :oneroom="원룸들[3]" />
    <!-- //카드 -->

  </div>
</template>

<script>
import data from './assets/oneroom'; // 확장자 생략 가능
import Discount from "./components/Discount";
import Modal from './components/Modal';
import Card from './components/Card';

export default {
  name: "App",
  data() {
    return {
      obj : {name : 'kim', age : '20'},
      idx : 0,
      원룸들 : data,
      price1 : 60,
      price2 : 70,
      스타일 : 'color: blue',
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      메뉴들 : ['Home', 'Shop', 'About'],
      신고수 : [0,0,0],
      visibleModal : false, // 모달창 상태, (0, 1로도 표현 가능)
    }
  },
  methods: {
    //함수 만드는 공간
    increase() {
      this.신고수 += 1; //함수안에서 data를 쓸 때는 무조건 앞에 this.를 붙이자 (this.데이터명)
    },
  },
  components: {
    Discount,
    Modal,
    Card,
  },
};
</script>

<style>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

#app {
  text-align: center;
}

.menu {
  background-color: palevioletred;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: #fff;
  font-size:17px;
  padding: 0 30px;
}

h4 {
  cursor: pointer;
}

.room-img {
  width: 100%;
}
</style>