<template>
    <div class="main">
        <div class="option-erea">
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
        <div class="edit-erea">
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

.option-erea {
    border-bottom: 1px solid;
    float: right;
    width: 100%;
}

.option-erea > button {
    background-color: white;
    border: none;
    
}

#talk-view {
    text-align: right;
    overflow-y: auto;
    width: 100%;
    height: calc(100vh - 270px);
    white-space: pre-wrap;
}

#talk-view > div {
    margin: 10px;
    display: flex;
    flex-direction: row-reverse;

}

#talk-view > div > p {
    background-color: aqua;
    padding: 10px;
    max-width: 75%;
    text-align: left;
}

.edit-erea {
    position: absolute;
    bottom: 5px;
    margin: 0 10px;
    height: 110px;
}

.edit-erea > textarea {
    width: 600px;
    height: 100px;
    resize: none;
    overflow-y: auto;
    margin-right: 10px;
}

.edit-erea > button {
    position: relative;
    bottom: 7px;
    border: none;
    background: white;
}

.edit-erea > textarea, button {
    display:inline-block;
}

</style>