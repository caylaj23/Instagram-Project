<template>
  <body>
    <div class="page-container">
      <h3>Username:</h3>
      <input type="text" v-model="username" />
      <h3>User Image:</h3>
      <input type="text" v-model="userImage"/>
      <h3>Image Link:</h3>
      <input type="text" v-model="postImage"/>
      <h3>Like:</h3>
      <input type="text" v-model="likes"/>
      <h3>Caption:</h3>
      <input type="text" v-model="caption"/>
      <button @click="submit()" class="button">Submit</button>
    </div>
     
    </body>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
const router = useRouter();


let username = ''
let likes = ''
let postImage = ''
let caption = ''
let userImage = '' 





function submit() {

  let textboxInfo = {
    "username" : username,
    "likes" : likes,
    "postimage" : postImage,
    "caption" : caption,
    "userimage" : userImage

  }
  const params = {
  method: "POST",
  headers: {
    Accept: "application/json",
    "Content-Type": "application/json",
  },

  body: JSON.stringify(textboxInfo),
};
  fetch("https://66ccd18b8ca9aa6c8cc8cbc0.mockapi.io/post", params)
    .then((response) => response.json())
    .then(info => console.log(info));
    

}
</script>

<style scoped>
.page-container {
  width: 300px;
}
.button {
  margin: 20px;
  background-color: rebeccapurple;
  color: black;
  width: 50px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-left: 60px;
}

body {
color: purple;
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
}
</style>
