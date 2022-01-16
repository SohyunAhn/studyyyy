<template>
  <div id="app">
    <Header />
<!--    <div id="content" class="content ">-->
<!--      <router-view />-->
<!--    </div>-->
    <div>
      원룸썁
      <h4>xx 원룸</h4>
      <p>{{ price1 }} 만원</p>
    </div>
    <div>
      <h4>xx 원룸</h4>
      <p>{{ price2 }} 만원</p>
    </div>
  </div>
</template>
<script>
import Header from './components/layout/Header'
// import Axios form

export default {
  name: 'App',
  data(){
    return{
      price1 : 60,
      price2 : 70,
    }
  },
  components: {
    Header,
  }
}
</script>