<template>
  <div class="row">
    <div class="card"
    v-show="dataInfo.data" 
    v-for="data in dataInfo.data" 
    :key="data.login"
    >
      <a :href="data.html_url" target="_blank">
        <img :src="data.avatar_url" style='width: 100px'/>
      </a>
      <p class="card-text">{{data.login}}</p>
    </div>
    <h2 v-show="dataInfo.isFirst">你好！歡迎來到此網站</h2>
    <h2 v-show="dataInfo.isloading">載入中。。。請稍後</h2>
    <h2 v-show="dataInfo.errormsg">載入發生錯誤 原因:{{dataInfo.errormsg}}</h2>
  </div>
</template>

<script>
  export default {
    name:'ShowList',
    data() {
      return {
        dataInfo:{
          isFirst:true,
          isloading:false,
          errormsg:'',
          data:[]
        }
      }
    },
    methods: {
      showListData(obj){
        // console.log(obj)
        this.dataInfo = {...this.dataInfo,...obj}
      }
    },
    mounted() {
      this.$bus.$on('showListData',this.showListData)
    },
  }
</script>

<style>
  .album {
    min-height: 50rem; /* Can be removed; just added for demo purposes */
    padding-top: 3rem;
    padding-bottom: 3rem;
    background-color: #f7f7f7;
  }

  .card {
    float: left;
    width: 33.333%;
    padding: .75rem;
    margin-bottom: 2rem;
    border: 1px solid #efefef;
    text-align: center;
  }

  .card > img {
    margin-bottom: .75rem;
    border-radius: 100px;
  }

  .card-text {
    font-size: 85%;
  }

</style>