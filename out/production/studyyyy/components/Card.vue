<template>
  <div>
    <img :src="oneroomList.image" class="room-img" />
    <h4>{{ oneroomList.title }}</h4>
    <p>{{ oneroomList.price }}원</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props : {
    원룸들 : Object,
  },
  data() {
    return {
    }
  },
  methods: {
  },
  components: {
  },
}
</script>

<style>

</style>