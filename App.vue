<template>
  <div id="app">
    <header @click="toggleFalse">
      <!-- <ul class="nav-items">
        <li>トーク</li>
        <li>お気に入り</li>
        <li>タグ</li>
        <li>同報</li>
        <li>校閲</li>
        <li>LOM</li>
        <li>Web</li>
        <li>ツール</li>
      </ul> -->
      <img src="../images/ヘッダー.png" alt="" height="100px">
    </header>

    <div class="test">
      <TalkSideBar @toggleF="toggleFalse" :newMsg="newMsg"/>
      <MainView @toggleF="toggleFalse" @toggle="toggle" @new-msg="inputNewMsg" @clear="clearMsg" @edit="edit" :editText="selectedMsg"/>
      <ProofreadingSideBar v-show="isShow" @selected-msg="inputMsg" @toggle="toggle"></ProofreadingSideBar>
    </div>

  </div>
</template>

<script>
import MainView from './components/MainView.vue'
import TalkSideBar from './components/TalkSideBar.vue'
import ProofreadingSideBar from './components/ProofreadingSideBar.vue'



export default {
  name: 'App',
  components: {
    MainView,
    TalkSideBar,
    ProofreadingSideBar
  },
  data: function(){
    return {
      isShow: false,
      selectedMsg: '',
      newMsg: []
    }
  },
  methods: {
    toggle: function(){
      this.isShow = !this.isShow
    },
    toggleFalse: function(){
      this.isShow = false;
    },
    clearMsg: function(){
      this.selectedMsg = ''
    },
    edit: function(msg){
      this.selectedMsg = msg
    },
    inputMsg: function(msg){
      this.selectedMsg = msg
    },
    inputNewMsg: function(msg){
      const temp = msg[0].split('\n');
      if(temp.length >= 2){
        this.newMsg = [`${temp[0]}\n${temp[1]}`, msg[1]]
      } else {
        this.newMsg = msg
      }
    }
  }
}
</script>

<style>
body{
  margin:0px;
}

header {
  background-color: rgb(30, 40, 71);
  color: gray;
  height: 100px;
  width: 100%;
  margin: 0;
}

.nav-items {
  margin: 0;
}

.nav-items > li {
  list-style: none;
  display: inline-block;
  width: 90px;
  font-size: 12px;
  text-align: center;
}

.test {
  display: flex;
}
</style>
