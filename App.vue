<template>
  <div id="app">
    <header></header>
    <div class="test">
      <TalkSideBar/>
      <MainView @toggle="toggle" @clear="clearMsg" @edit="edit" :editText="selectedMsg"/>
      <ProofreadingSideBar v-show="isShow" @selected-msg="inputMsg"></ProofreadingSideBar>
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
      selectedMsg: ''
    }
  },
  methods: {
    toggle: function(){
      this.isShow = !this.isShow
    },
    clearMsg: function(){
      this.selectedMsg = ''
    },
    edit: function(msg){
      this.selectedMsg = msg
    },
    inputMsg: function(msg){
      this.selectedMsg = msg
    }
  }
}
</script>

<style>
body {
  margin: 0;
}

header {
  height: 100px;
  background-color: blue;
}

.test {
  display: flex;
}


</style>
