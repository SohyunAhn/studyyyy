<template>
  <div id="app">
<!--    <Header/>-->
    <div id="content" class="content">
<!--      <router-view></router-view>-->

      <div class="menu">
        <a v-for="(menulist,i) in menus" :key="i">{{ menulist }}</a>
      </div>

      <div class="black-bg" v-if="modalState == true">
        <div class="white-bg">
          <h4>상세페이지</h4>
          <img :src="rooms[openpop].image" alt="room-img" class="roomimg">
          <p>{{ rooms[openpop].content }}</p>
          <button @click="modalState = false">닫기</button>
        </div>
      </div>

      <div v-for="(a,i) in rooms" :key="i">
        <img :src="a.image" alt="room-img" class="roomimg">
        <h4 @click="modalState = true; openpop = i">{{a.title}}</h4>
        <p>{{a.price}}원</p>
      </div>

      <hr>

      <p>{{products[0]}}</p>
      <p>{{products[1]}}</p>
      <p>{{products[2]}}</p>

      <hr>

      <div v-for="(a,i) in products" :key="i">
        <h4>{{a}}</h4>
        <p>60</p>
      </div>
      <div>{{price1}}만원</div>
      <div>{{price2}}만원</div>

      <div>
        <p @click="modalState = true">{{products[0]}}</p>
        <p>60만원</p>
        <button v-on:click="신고수[0]++">신고하기</button>
        <span>신고수 : {{신고수[0]}}</span>
      </div>
      <div>
        <p>{{products[1]}}</p>
        <p>50만원</p>
        <button @click="신고수[1]++">신고하기</button>
        <span>신고수 : {{신고수[1]}}</span>
      </div>
      <div>
        <p>{{products[2]}}</p>
        <p>30만원</p>
        <button @click="신고수[2]++">신고하기</button>
        <span>신고수 : {{신고수[2]}}</span>
      </div>
    </div>
  </div>
</template>

<script>
// import Header from "./components/layout/header.vue";

import data from './assets/data.js';

export default {
  name: "App",
  data(){
    return{
      rooms: data,
      modalState: false,
      openpop: 0,
      price1: 60,
      price2: 70,
      products: ['역삼동원룸','천호동원룸','망원동원룸'],
      menus: ['home','shop','about'],
      신고수: [0,0,0],
    }
  },
  methods: {
    increase(){
      this.신고수 += 1
    },
  },
  components: {
    // Header,
  }
};
</script>

<style>
body{padding:0;margin:0;}
div{box-sizing:border-box;}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding:50px 0;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.menu{background:darkgoldenrod;padding:15px;border-radius:5px;}
.menu a{color:#fff;padding:5px;}

.black-bg{position:fixed;width:100%;height:100%;padding:20px;background:rgba(0,0,0,0.5);}
.white-bg{pwidth:100%;padding:20px;background:#fff;border-radius:8px;}
.roomimg{width:300px}
</style>
