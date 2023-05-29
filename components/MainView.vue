<template>
    <div class="main">
        <div class="option-area">
            <div>
                <img class="icon" src="../../images/人型アイコン.png" width="60px" height="60px">
                <div class="option-title">
                    <p class="option-title-name">牛久 朝之</p>
                    <p class="option-title-class">人事・労務 Team</p>
                </div>
            </div>
            <button @click="$emit('toggle')">
                <img src="../../images/ロボットアイコン.png" alt="校閲機能表示ボタン" width="30px" height="30px">
            </button>
        </div>
        <div>
            <div id="talk-view">
                <div v-for="(msg, index) in msgList" :key="index">
                    <p>{{ msg }}</p>
                </div>
            </div>
        </div>
        <div class="edit-area">
            <textarea v-model="Text"></textarea>
            <button @click="submit">
                <img src="../../images/紙飛行機アイコン.png" alt="送信アイコン" width="30px" height="30px">
            </button>
        </div>
    </div>
</template>

<script>
export default {
    name: "MainView",
    data: function(){
        return {
            msgList: [],
            Text: '',
        }
    },
    props: {
        editText: String
    },
    watch: {
        editText(){
            this.Text = this.editText;
        },
    },
    methods: {
        submit: function(){
            if(this.Text.trim()){
                this.msgList.push(this.Text);
            }
            const temp = document.getElementById("talk-view"), tem = temp.scrollHeight
            temp.scrollTo(0, tem+80)

            this.Text = '';
            this.$emit('clear')
        },
    }
}
</script>


<style scoped>
.main {
    display: inline-block;
    /* background-color: rgb(242, 241, 241); */
    width: 100%;
    height: calc(100vh - 100px);
    margin: 0;
}

.option-area {
    float: right;
    width: 100%;
    position: relative;
    height: 60px;
}

.option-area > div {
    display: inline-block;
}

.icon {
    margin: 0 5px;
}

.option-title {
    display: inline-block;
    position: absolute;
    bottom: 5px;
}

.option-title-name {
    font-size: 23px;
    margin: 0;
    line-height: 1;
}

.option-title-class {
    font-size: 5px;
    color: gray;
    margin: 0;
}

.option-area > button {
    background-color: white;
    border: none;
    position: absolute;
    top: 25%;
    right: 20px;
}

#talk-view {
    text-align: right;
    overflow-y: auto;
    width: 100%;
    height: calc(100vh - 290px);
    white-space: pre-wrap;
}

#talk-view > div {
    margin: 10px;
    display: flex;
    flex-direction: row-reverse;

}

#talk-view > div > p {
    background-color: rgb(172, 192, 227);
    padding: 10px;
    max-width: 75%;
    text-align: left;
    border-radius: 2px;
}

.edit-area {
    position: absolute;
    bottom: 5px;
    margin: 0 10px;
    height: 110px;
}

.edit-area > textarea {
    width: 900px;
    height: 100px;
    resize: none;
    overflow-y: auto;
    margin-right: 10px;
    border-radius: 15px;
}

.edit-area > button {
    position: relative;
    bottom: 7px;
    border: none;
    background: white;
}

.edit-area > textarea, button {
    display:inline-block;
}

</style>
