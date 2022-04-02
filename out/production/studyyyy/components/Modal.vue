<template>
  <div class="black-bg" v-if="visibleModal == true">
    <div class="white-bg">
      <h4>{{ 원룸들[idx].title }}</h4>
      <div>
        <img :src="원룸들[idx].image" alt="" class="room-img">
      </div>
      <p>{{ 원룸들[idx].content }}</p>
      <p>{{ 원룸들[idx].price }}원</p>
      <Discount />
      <!--  <button @click="visibleModal = false">닫기</button>-->
    </div>
  </div>
</template>

<script>
import Discount from "./Discount";

export default {
  name: "Modal",
  props: {
    원룸들 : Array, // 배열
    idx : Number, // 숫자
    visibleModal: Boolean, // true, false
  },
  data() {
    return {
    }
  },
  methods: {
  },
  components: {
    Discount,
  },
}
</script>

<style>
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