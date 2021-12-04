<template>
  <div class="vuex">
    <h1>Sample 화면입니다.</h1>
  </div>
</template>

<script>
import http from "../http";

export default {
  name: "Vuex",
  components: {},
  data() {
    return {
      items: [],
      totalItems: 0,
      totalPages: 0,
    }
  },
  methods: {
    delete(id) {
      http
          .delete("/api/sample/sample/" + id)
          .then(response => {
            const { data } = response
            console.log(data)
          })
          .catch(error => {
            alert(error)
          })
    },
    create(id, params) {
      http
          .post("/api/sample/sample/", params)
          .then(response => {
            const { data } = response
            console.log(data)
          })
          .catch(error => {
            alert(error)
          })
    },
    update(id, params) {
      http
          .put("/api/sample/sample/" + id, {
            params: params,
          })
          .then(response => {
            const { data } = response
            console.log(data)
          })
          .catch(error => {
            alert(error)
          })
    },
    read() {
      let params = {}
      http
          .get("/api/sample/sample", {
            params: params,
          })
          .then(response => {
            const { data } = response
            console.log(data)
            this.items = data.items
            this.totalItems = data.totalItems
            this.totalPages = data.totalPages
          })
          .catch(error => {
            alert(error)
          })
    },
  },
  created() {
    console.log(http)
    this.read()
  },
}
</script>

<style scoped>
  .main{padding:100px;border:5px solid #000;}
</style>