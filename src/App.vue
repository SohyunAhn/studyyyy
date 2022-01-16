<template>
  <div id="app">

    <div class="black-bg" v-if="visibleModal == true">
      <div class="white-bg">
        <h4>상세페이ㅣ지임</h4>
        <p>그렇다</p>
        <button @click="visibleModal = false">닫기</button>
      </div>
    </div>

    <div class="menu">
      <a v-for="menuList in 메뉴들" :key="menuList">{{ menuList }}</a>
    </div>

    <div v-for="(oneroomList,i) in 원룸들" :key="i">
      <img :src="oneroomList.image" alt="room-img">
      <h4 @click="visibleModal = true">{{ oneroomList.title }}</h4>
      <p>{{ oneroomList.price }}원</p>
    </div>

  </div>
</template>

<script>
import data from './assets/oneroom'; //.js확장자 생략 가능

export default {
  name: "App",
  data() {
    return {
      원룸들 : data,
      price1 : 60,
      price2 : 70,
      스타일 : 'color: blue',
      products: ['역삼동 원룸', '천호동 원룸', '마포구 원룸'],
      메뉴들 : ['Home', 'Shop', 'About'],
      신고수 : [0,0,0],
      visibleModal : false,
    }
  },
  methods: {
    //함수 만드는 공간
    increase() {
      this.신고수 += 1; //함수안에서 data를 쓸 때는 무조건 앞에 this.를 붙이자 (this.데이터명)
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

.black-bg {
  position: fixed;
  padding: 20px;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
}

.white-bg {
  width: 100%;
  background-color: #fff;
  padding: 20px;
  border-radius: 10px;
}

</style>