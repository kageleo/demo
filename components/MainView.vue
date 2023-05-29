<template>
    <div class="main">
        <div class="option-area" @click="$emit('toggleF')">
            <div>
                <img class="icon" src="../../images/人型アイコン.png" width="60px" height="60px">
                <div class="option-title">
                    <p class="option-title-name">牛久 朝之</p>
                    <p class="option-title-class">人事・労務 Team</p>
                </div>
            </div>
        </div>
        <button class="ai" @click="$emit('toggle')">
            <img src="../../images/ロボットアイコン1.png" alt="校閲機能表示ボタン" width="30px" height="30px">
        </button>
        <button class="option-1">
            <img src="../../images/パソコンアイコン.png" width="30px" height="30px">
        </button>
        <button class="star">
            <img src="../../images/星アイコン.png" width="30px" height="30px">
        </button>
        <button class="option-3">
            <img src="../../images/三点アイコン1.png" width="30px" height="30px">
        </button>
        <div @click="$emit('toggleF')">
            <div id="talk-view">
                <div class="msg-view" v-for="(msg, index) in msgList" :key="index">
                    <img src="../../images/人型アイコン２.png" width="40px" height="37px">
                    <div>
                        <p class="my-name">ラキール君</p>
                        <div class="msg-body">
                            <p class="msg-text">{{ msg[0] }}</p>
                            <p class="msg-date">
                                {{ msg[1] }}
                                &nbsp;&nbsp;&nbsp;<img src="../../images/タグアイコン.png" width="9px" height="9px">
                                &nbsp;<img src="../../images/矢印.png" width="10px" height="10px">
                            </p>
                        </div>
                    </div>
                </div>
                <!-- <p id="bottom-scroll"></p> -->
            </div>
        </div>
        <div class="edit-area" @click="$emit('toggleF')">
            <button>
                <img src="../../images/クリップアイコン.png" width="40px" height="40px">
            </button>
            <textarea v-model="Text"></textarea>
            <button @click="submit">
                <img src="../../images/紙飛行機アイコン.png" alt="送信アイコン" width="40px" height="40px">
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
        }
    },
    methods: {
        submit: function(){
            if(this.Text.trim()){
                const now = new Date();
                
                const Year = now.getFullYear();
                const Month = now.getMonth()+1;
                const Day = now.getDate();
                const Hour = now.getHours();
                const Min = Number(now.getMinutes()) >= 10 ? now.getMinutes() : `0${now.getMinutes()}` ;

                const time = `${Year}/${Month}/${Day} ${Hour}:${Min}`;

                this.msgList.push([this.Text, time]);
            }
            
            const element = document.getElementById("talk-view")
            const temp = element.scrollHeight

            setTimeout(function(){
                element.scrollTo(0, temp)
            },50);

            console.log(this.msgList[this.msgList.length - 1])

            this.$emit('new-msg', this.msgList[this.msgList.length - 1])
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

.ai {
    background-color: white;
    border: none;
    position: absolute;
    top: 110px;
    right: 175px;
}

.option-1 {
    background-color: white;
    border: none;
    position: absolute;
    top: 112px;
    right: 120px;
}

.star {
    background-color: white;
    border: none;
    position: absolute;
    top: 110px;
    right: 65px;
}

.option-3 {
    background-color: white;
    border: none;
    position: absolute;
    top: 110px;
    right: 10px;
}

#talk-view {
    text-align: right;
    overflow-y: auto;
    width: 100%;
    height: calc(100vh - 320px);
    white-space: pre-wrap;
}

.msg-view {
    margin: 0 5px 5px 0;
    min-height: 40px;
    position: relative;
}

.msg-view > img {
    position: absolute;
    top: 0;
    right: calc(75% + 2px);
}

.msg-view > div {
    display: inline-block;
    width: 75%;
    text-align: left;
}

.my-name {
    font-size: 5px;
    margin: 0;
    line-height: 1.2;
}

.msg-body {
    display: inline-block;
    /* flex-direction: row-reverse; */
    width: 100%;
    background-color: rgb(172, 192, 227);
    border-radius: 3px;
}

.msg-body > p {
    text-align: left;
    margin: 0;
}

.msg-text {
    padding: 0;
    padding-left: 7px;
    padding-top: 8px;
    line-height: 1.2;
}

.msg-date {
    color: gray;
    font-size: 5px;
    padding: 0;
    padding-left: 7px;
}

#bottom-scroll {
    height: 30px
}

.edit-area {
    position: absolute;
    bottom: 20px;
    margin: 0 10px;
    height: 110px;
}

.edit-area > textarea {
    width: 1000px;
    height: 100px;
    resize: none;
    overflow-y: auto;
    margin: 0 15px;
    border-radius: 15px;
    padding: 10px;
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
