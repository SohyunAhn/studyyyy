<template>
  <div id="app">
    <Header />
<!--    <div id="content" class="content ">-->
<!--      <router-view />-->
<!--    </div>-->
    <div class="menu">
      <a v-for="item in 메뉴들" :key="item">{{ item }}</a>
    </div>
    <div class="black-bg" v-if="모달창열렸니 == true" @click="모달창열렸니 = false">
      <div class="white-bg" >
        <h4>상세페이지임</h4>
        <p>상세페이지상세</p>
      </div>
    </div>
<!--    <div v-for="(item, i) in products" :key="i">-->
<!--      <h4 @click="모달창열렸니 = true" class="red" :style="스타일">{{ item }} 원룸</h4>-->
<!--      <p>50 만원</p>-->
<!--    </div>-->

    <div v-for="(item, i) in 원룸들" :key="i" @click="모달창열렸니 = true">
      <img :src="item.image" class="room-img">
      <h4 > {{item.title}}</h4>
      <p class="cnt">{{item.content}}</p>
      <p class="price">{{item.price}} 원</p>

    </div>


<!--    <div >-->
<!--      <img src="./assets/logo.png">-->
<!--      <h4 class="red" @click="모달창열렸니 = true">{{ products[0] }}</h4>-->
<!--      <p>50 만원</p>-->
<!--      <button @click="신고수[0] += 100">허위매물신고111</button><span>신고수 : {{신고수[0]}}</span>-->
<!--    </div>-->
<!--    <div>-->
<!--      <h4 class="red" >{{ products[1] }}</h4>-->
<!--      <p>60 만원</p>-->
<!--      <button @click="신고수[1]++">허위매물신고</button><span>신고수 : {{신고수[1]}}</span>-->
<!--    </div>-->
<!--    <div>-->
<!--      <h4 class="red" >{{ products[2] }}</h4>-->
<!--      <p>70 만원</p>-->
<!--      <button @click="신고수[2]++">허위매물신고</button><span>신고수 : {{신고수[2]}}</span>-->
<!--    </div>-->
  </div>
</template>
<script>
import Header from './components/layout/Header'
// import Axios form
import data from './oneroom'

export default {
  name: 'App',
  data(){
    return{
      원룸들 : data,
      모달창열렸니 : false,
      메뉴들 : ['Home', 'Shop', 'About'],
      products: ['역삼동원룸', '천호동원룸', '관악구원룸'],
      신고수 : [0, 0, 0],
    }
  },
  components: {
    Header,
  },
  methods: {
    increase(){
      this.신고수 ++;
    }
  },
}
</script>
<style>
div { box-sizing: border-box;}
.black-bg {width: 100%; height: 100%; background: rgba(0,0,0,0.5); position: fixed; padding: 20px;}
.white-bg {width: 100%; background: #fff; border-radius: 10px; padding: 50px; text-align: center;}
.menu {background: darkslateblue; padding: 15px; border-radius: 5px;}
.menu > a {color: #fff; padding: 10px;}
.room-img {width: 100%;}
.room-img:not(:first-child) {margin-top: 20px;}
.price {font-weight: 500;}
</style>
