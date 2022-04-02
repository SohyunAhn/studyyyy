<template>
  <div>
    <img :src="room.image" alt="room-img" class="roomimg">
    <h4 @click="evt">{{room.title}}</h4>
<!--    $~~~ 는 vue의 변수 / emit 부모에게 보내는 메세지-->
<!--    <h4 @click="modalState = true; openpop = i">{{a.title}}</h4>-->
    <p>{{room.price}}원</p>
  </div>
</template>

<script>
export default {
  name: "card",
  props: {
    room: Object,
  },
  methods: {
    evt(){
      this.$emit('openModal', this.room.id)
    }
  }
}
</script>

<style scoped>

</style>