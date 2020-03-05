<template>
    <div id="box">
        <li v-for="(message, index) in messages" :key="index">{{message.value}}</li>
        <!-- messages displayed here -->
    </div>
</template>

<script>
export default {
    props: ["messages"]
};
</script>

<style scoped>
/* #box {
    background: #000;
    width: 500px;
    height: 300px;
    color: white;
}
#box li {
    font-family:Georgia, 'Times New Roman', Times, serif;
    padding: 10px 20px;
    box-shadow: grey 30px 500;
} */
</style>