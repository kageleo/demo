<template>
  <div class="proofreading-side-bar">
    <div class="title-area">
      <input type="text" v-model="title" placeholder="要件を入力してください">
      <button @click="createMsg">作成</button>
    </div>
    <div class="suggestion-area">
      <div v-for="(suggestion, index) in suggestions" :key="index" @click="selectedMsg(index)">
        <p>{{ suggestion }}</p>
      </div>
    </div>
  </div>
</template>

<script>
import json from "../Test.json";

export default {
  name: 'ProofreadingSideBar',
  data: function(){
    return {
      title: '',
      suggestions: Object,
    }
  },
  methods: {
    createMsg: function(){
      if(this.title.trim()){
        this.suggestions = this.title in json ? json[this.title].messages : {"error": "現在そのワードに対する文章を作成できません。"}
      }
      this.title = '';
    },
    selectedMsg: function(index){
      this.$emit('selected-msg', this.suggestions[index])
      this.$emit('toggle')
      this.suggestions = {}
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.proofreading-side-bar {
  background-color: rgb(33, 62, 100);
  height: calc(100vh - 100px);
  width: 650px;
  position: absolute;
  right: 0;
}

.title-area {
  margin: 10px;
}

.title-area > input {
  width: 200px;
  margin-right: 5px;
}

.suggestion-area {
  height: calc(100vh - 170px);
  overflow: auto;
  margin-top: 10px;
}

.suggestion-area > div {
  background-color: white;
  margin: 8px;
  border-radius: 1px;
  white-space: pre-wrap;
}
</style>
