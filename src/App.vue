<template>
  <div id="app">
<!--    <Header/>-->
    <div id="content" class="content">
<!--      <router-view></router-view>-->

      <div class="menu">
        <a v-for="(menulist,i) in menus" :key="i">{{ menulist }}</a>
      </div>

      <Discount />
<!--      <Discount :name="object.name" :age="object.age"/>-->
<!--      <Discount v-bind="object"/>-->
<!--      <Discount :작명="데이터이름" :데이터이름="데이터이름" />-->
<!--      <Discount 데이터이름="[123,123]" 데이터이름="안녕하세요" />-->

      <div v-if="1 == 2">
        헬로오오
      </div>
      <div v-else>
        hi
      </div>

      <button @click="priceSort">가격순 정렬</button>

<!--      <div class="start" :class="{ end : modalState }">-->
      <transition name="fade">
        <Modal @closeModal="modalState = false;" :rooms="rooms" :openpop="openpop" :modalState="modalState" />
      </transition>
<!--      </div>-->
<!--      <Modal v-bind:rooms="rooms" />-->

      <Card @openModal="modalState = true; openpop = $event;" :room="rooms[i]" v-for="(a,i) in rooms" :key="i" />
<!--      <Card :a="rooms[0]" />-->
<!--      <Card :a="rooms[1]" />-->

      <hr>

      <p>{{products[0]}}</p>
      <p>{{products[1]}}</p>
      <p>{{products[2]}}</p>

      <hr>

<!--      <div v-for="(a,i) in products" :key="i">-->
<!--        <h4>{{a}}</h4>-->
<!--        <p>60</p>-->
<!--      </div>-->
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
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

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
      object: { name:'kim', age:20 }
    }
  },
  methods: {
    increase(){
      this.신고수 += 1
    },
    priceSort(){
      // this.rooms.sort()
      var array = [3, 5, 2];
      array.sort(function(a,b){
        return a - b;
      });

    },
  },
  components: {
    // Header,
    Discount : Discount,
    Modal : Modal,
    Card,
  }
};
</script>

<style>

.fade-leave-from {opacity:1;} /*시작시 스타일*/
.fade-leave-active {transition:all 6s;} /*효과*/
.fade-leave-to {opacity:0;} /*종료시 스타일*/

.fade-enter {opacity:0;} /*시작시 스타일*/
.fade-enter-active {transition:all 1s;} /*효과*/
.fade-enter-to {opacity:1;}

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

.black-bg{position:fixed;top:0;width:100%;height:100%;padding:20px;background:rgba(0,0,0,0.5);}
.white-bg{pwidth:100%;padding:20px;background:#fff;border-radius:8px;}
.roomimg{width:300px}

.start{opacity:0;transition:all 1s;}
.end{opacity:1;}
</style>
