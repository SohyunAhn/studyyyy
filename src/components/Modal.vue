<template>
  <div class="black-bg" v-if="visibleModal == true">
    <div class="white-bg">
      <h4>{{ 원룸들[idx].title }}</h4>
      <div>
        <img :src="원룸들[idx].image" alt="" class="room-img">
      </div>
      <p>{{ 원룸들[idx].content }}</p>
      <div>
        <!-- <input @input="month = $event.target.value" type="number" /> -->
<!--        <input v-model="month" type="number" />-->
        <input v-model.number="month" type="text">
      </div>
      <div>
<!--        <select v-model="month">-->
<!--          <option>11</option>-->
<!--          <option>22</option>-->
<!--          <option>33</option>-->
<!--        </select>-->
      </div>
      <div>
<!--        <input type="checkbox" v-model="month">-->
      </div>

      <p> {{ month }}개월 선택함 : {{ 원룸들[idx].price + month }}원</p>
      <Discount />
      <button @click="close()">닫기</button>
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
      month : 1, // 문자로 받을거면 초기값을 문자로 하자
      //month : '', // input checkbox는 boolean이기 때문에 공백으로 놓자

    }
  },
  methods : {
    close() {
      this.$emit('closeModal');
    },
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