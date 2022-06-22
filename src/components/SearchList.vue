<template>
  <section class="jumbotron">
    <h3 class="jumbotron-heading">Search Github Users</h3>
    <div>
      <input type="text" placeholder="enter the name you search" v-model="inputName" />&nbsp;
      <button @click="getList">Search</button>
    </div>
  </section>
</template>

<script>
  import axios from "axios";
  export default {
    name:'SearchList',
    data() {
      return {
        inputName:''
      }
    },
    methods: {
      getList(){
        this.$bus.$emit('showListData',{isFirst:false,isloading:true,errormsg:'',data:[]})
        axios.get(`https://api.github.com/search/users?q=${this.inputName}`).then(
          res => {
            console.log(res.data)
            this.$bus.$emit('showListData',{isloading:false,errormsg:'',data:res.data.items})
          },
          err => {
            // console.log('@',err.message)
            this.$bus.$emit('showListData',{isloading:false,errormsg:err.message,data:[]})
          }
        )
      },
    },
  }
</script>
