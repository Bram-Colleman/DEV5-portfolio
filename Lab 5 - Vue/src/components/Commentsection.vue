<script setup>
import { ref, onMounted } from 'vue';

const comments = ref([]);
onMounted(() => {
    fetchComments();
});

const fetchComments = async () => {
    const response = await fetch(`https://dev5-lab4-1hlz.onrender.com/api/v1/messages`);
    const res = await response.json();

    res.data.messages.forEach(message => {
        comments.value.push(message);
    });
    console.log(comments.value);
};

const send = () => {
    
}

</script>
<template>
<ul>
    <li v-for="comment in comments">
        <p><strong>{{ comment.user }}</strong></p>
        <p>{{ comment.text }}</p>
    </li>
</ul>
<div class="add">
    <input type="text" name="" id="">
    <button id="send" @click="send">Send</button>
</div>
</template>
<style scoped>
ul {
    height: 75vh;
    width: 50vw;
    list-style: none;
    overflow-y: scroll;
    background-color: #f8f8f8;
    margin: 0;
}
.add {
    height: 5vh;
    display: flex;
    flex-grow: 1;
}
input {
    width: 45vw;
}
button {
    width: 5vw;
    height: 5vh;
    display: flex;
    flex-grow: 1;
    align-self: center;
    justify-content: center;
    align-items: center;
}
p {
    margin: 0;
}
li {
    margin: 1rem;
}
</style>