<template>
  <div class="black-bg" v-if="modalState == true">
    <div class="white-bg">
      <h4>{{ rooms[openpop].title }}</h4>
      <img :src="rooms[openpop].image" alt="room-img" class="roomimg">
      <p>{{ rooms[openpop].content }}</p>
<!--      <input @input="month = $event.target.value">-->
      <input v-model="month">
      <p>{{ month }}개월 선택하셨습니다.</p>
      <p>{{ rooms[openpop].price }}원</p>
      <p>총 금액 : {{ rooms[openpop].price * month }}원</p>
      <button @click="$emit('closeModal')">닫기</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Modal",
  data() {
    return{
      month: 1,
    }
  },
  watch: { //데이터감시 감시할데이터(){}
    month(a){
      //month라는 데이터가 변할떄마다 month() 안에 코드가 실행됨
      //사용자가 month를 텍스트로 입력하는지 확인하기
      if(isNaN(a) == true){
        alert('문자입력불가');
        this.month = 1;
      }
      //입력한 데이터가 13보다 크면 경고문 띄우기
      // if(a >= 13) {
      //   alert('13개월이상 입력하실수없습니다')
      //   this.month = 1;
      // }
    }
  },
  props: { //props는 read-only
    // 데이터이름 : 자료형
    rooms : Array,
    openpop: Number,
    modalState: Boolean,
  },
}
</script>

<style scoped>

</style>