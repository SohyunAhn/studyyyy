<template>
  <div>
    <h1>Welcome to {{title}} </h1>
    <input type="text" v-model="input1" >
    <button type="button" @click="getData" >get</button>
    <button type="button" @click="setData" >set</button>

    <select class="form-select" v-model="name" @change="changeName">
      <option :key="i" :value="d.v" v-for="(d,i) in options">{{d.t}}</option>
    </select>

    <table class="table table-bordered" v-if="tableShow ">
      <tr :key="i" v-for="(d,i) in options">
        <td>{{d.v}}</td>
        <td>{{d.t }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return{
      title :'려경 뷰 공부하기',
      title2 : '가디',
      input1 :'abc',
      options :[
        {v:"H", t:"hong"},
        {v:"K", t:"kim"},
        {v:"A", t:"Ahn"},
      ],
      name: "K",
      tableShow : true,
    }
  },
  watch: {
    input1() {
      console.log(this.input1)
    }
  },
  methods: {
     getData() {
       alert(this.input1);
     },
    setData() {
       this.input1 = '12345'
    },
    changeName() {
       alert(this.name );
    }
  },
  beforeCreate() {
    console.log('beforeCreate');
  },
  created() {
    console.log('created');
  },
  beforeMount() {
    console.log('beforeMount');
  },
  mounted() {
    console.log('mounted');
  },
  beforeUpdate() {
    console.log('beforeUpdate');
  },
  updated() {
    console.log('updated');
  },
  beforeDestroy() {
    console.log('beforeDestroy');
  },
  destroyed() {
    console.log('de stroyed');
  }
};
</script>
