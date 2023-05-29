<template>
    <div id="talk-side-bar" @click="$emit('toggleF')">
        <ul>
            <li>
                <div class="menbers">
                    <img src="../../images/人型アイコン.png" width="55px" height="55px">
                    <div class="talk-div">
                        <p class="talk-title">牛久 朝之</p>
                        <div class="pp">
                            <p class="talk-msg">{{ newMsg[0] }}</p>
                        </div>
                        <div class="pp pp-date">
                            <p class="talk-date">{{ newMsg[1] }}</p>
                        </div>
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'TalkSideBar',
    props: {
        newMsg: []
    }
}
</script>

<style scoped>
#talk-side-bar {
    width: 500px;
    height: calc(100vh - 100px);
    background-color: rgb(33, 62, 100);
}

#talk-side-bar > ul {
    padding-left: 0;
    text-align: center;
    margin: 0;
}

li {
    list-style: none;
    height: 60px;
    color: black;
    font-size: 17px;
    line-height: 3;
    background-color:  white;
}

li > div {
    display: flex;
}

img {
    display: inline-block;
    margin: 2px 2px 0 3px;
}

.talk-div {
    text-align: left;
}

p {
    margin: 0;
    line-height: 1;
}

.talk-title {
    margin-top: 8px;
}

.talk-msg {
    color: gray;
    margin-top: 2px;
    font-size: 12px;
    white-space: pre-wrap;
    position: absolute;
    top: 26px;
    line-height: 1.2;
    width: 200px;
}

.talk-date {
    color: gray;
    margin-top: 2px;
    font-size: 10px;
    width: 90px;
    position: absolute;
    right: 0;
    bottom: 27px;
}

.pp {
    display: inline-block;
}

.menbers {
    position: relative;
}

</style>
