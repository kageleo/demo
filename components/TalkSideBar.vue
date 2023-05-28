<template>
    <div class="talk-side-bar">
        <ul>
            <li>上司</li>
        </ul>
    </div>
</template>

<script>

export default {
    name: "TalkSideBar",
}
</script>

<style scoped>

.talk-side-bar {
    display: inline-block;
    background-color: aqua;
    width: 300px;
    height: calc(100vh - 100px);
}

.talk-side-bar > ul {
    margin: 0;
    padding-left: 0;
    text-align: center;
}

.talk-side-bar > ul > li {
    list-style: none;
    height: 50px;
    line-height: 3;
}

</style>