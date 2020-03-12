<template>
    <div id="message-app" class="center">
        <h1>Chatbox</h1>
        <div id="box">
            <li v-for="(message, index) in messages" :key="index">{{message.value}}</li>
        </div>
        <!-- messages displayed here -->
    </div>
</template>

<script>
export default {
    props: ["messages"]
};
</script>

<style scoped>
#message-app {
    width: 500px;
    height: 300px;
    padding: 20px;
}
#box {
    margin: 10px 0;
    border: solid black 2px;
}
#box li {
    font-family:Georgia, 'Times New Roman', Times, serif;
    padding: 10px 20px;
    box-shadow: grey 30px 500;
    list-style: none;
}
.center {
    margin: auto;
}
</style>