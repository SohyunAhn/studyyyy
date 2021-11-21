<template>
  <div class="home">
    <h1>welcom to {{title2}}!</h1>
    <input type="text" v-model="input1" />
    <button type="button" @click="getData">Get</button>
    <button type="button" @click="setData">Set</button>
<!--    <P>result: {{this.input1}}</P>-->

<!--    <ul>-->
<!--      <li :key="idx" v-for="(item, idx) in options">-->
<!--        {{item.t}}-->
<!--      </li>-->
<!--    </ul>-->

    <select class="form-control" v-model="region" @change="changeRegion">
      <option :key="idx" :value="item.v" v-for="(item, idx) in options">{{item.t}}</option>
    </select>

    <table class="table table-bordered" v-show="tableShow">
      <tr :key="idx" v-for="(item, idx) in options">
        <td>{{item.t}}</td>
        <td>{{item.v}}</td>
      </tr>
    </table>

  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "개발자의 품격",
      title2: "Seoul",
      input1: "abcd",
      options: [
        {v:"S", t:"Seoul"},
        {v:"J", t:"Jeju"},
        {v:"I", t:"Iisan"},
      ],
      region: "J",
      tableShow: false,
    };
  },
  watch: {
    input1() {
      console.log(this.input1);
    },
    title() {
      // console.log(this.title);
    }
  },
  methods: {
    getData() {
      alert(this.input1);
    },
    setData() {
      this.input1 = "12345";
    },
    changeRegion() {
      alert(this.region);
    },
  },
  beforeCreate() {
    console.log("beforeCreate");
  },
  created() {
    console.log("created");  //best
  },
  beforeMount() {
    console.log("beforeMount");
  },
  mounted() {
    console.log("mounted"); //best
  },
  beforeUpdate() {
    // console.log("beforeUpdate");
  },
  updated() {
    // console.log("updated");
  },
  beforeDestroy() {
    console.log("beforeDestroy");
  },
  destroyed() {
    console.log("destroyed");
  }
};
</script>
