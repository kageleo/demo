<template>
    <div id="talk-side-bar">
        <ul>
            <li>
                <div>
                    <img src="../../images/人型アイコン.png" width="55px" height="55px">
                    <div>
                        <p class="talk-title">牛久 朝之</p>
                        <p class="talk-msg"></p>
                    </div>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'TalkSideBar'
}
</script>

<style scoped>
#talk-side-bar {
    width: 300px;
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
    font-size: 10px;
}

</style>
