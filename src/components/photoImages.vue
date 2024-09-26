<script setup>
import { ref } from 'vue';

const props = defineProps(["photoImages"]);


const likedPhoto = ref(false)
const likes = ref(props.photoImages.likes)

function likeButton(){
if (likedPhoto.value){
  likes.value--
} else {
  likes.value++
}
likedPhoto.value = !likedPhoto.value
updateLikes()
}


function updateLikes(){
const params = {
method: "PUT",
body: JSON.stringify({likes: likes.value}),
headers: {
Accept: "application/json",
"Content-Type": "application/json"
}
}

fetch(`https://66ccd18b8ca9aa6c8cc8cbc0.mockapi.io/post/${props.photoImages.id}`, params)
.then(response => {return response.json()})
.then(data =>{
  if (data) {
    props.photoImages.likes = data.likes
  }
}) 
}


</script>

<template>
<body>
<div class="photos-container">
<div class="header">
<img class="user-icon" :src="photoImages.userimage" >
<p class="username-text">{{ photoImages.username }}</p>
</div>
<div class="user-image">
<img class="image" :src="photoImages.postimage" />
<div class="like-section">
  <img class="heart-image" v-if="likedPhoto" @click="likeButton()" src="../assets/heart-icon.png">
<img v-else @click="likeButton()" class="gray-heart" src="../assets/gray-heart.jpeg">

<p class="like">{{ photoImages.likes }} likes</p>
</div>
</div>
<div class="lower-container">
<p class="comment-area"><span class="username-text">{{photoImages.username}}:</span> {{ photoImages.caption }}</p>

</div>
</div>
</body>
</template>

<style scoped>
.photos-container {
display: flex;
flex-direction: column;
width: 400px;
margin-top: 50px;
border-radius: 15px;
border: 2px solid yellow;
box-shadow: 6px 8px 8px yellow;
margin-bottom: 40px;
}
.header {
display: flex;
margin-left: 3px;
}

.user-icon {
border-radius: 50%;
width: 30px;
height: 45px;
padding: 4px;

}
img {
height: 300px;
width: 400px;


}
.lower-container {
width: 400px;
}

.comment-area {
margin-left: 8px;
}

.username-text, .like, .username-text {
font-weight: bold;
}

body {
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
}

.like-section {
display: flex;

}

.heart-image {
height: 20px;
width: 20px;
margin-top: 15px;
padding-left:9px;
padding-right: 4px;
fill: red;
}

.gray-heart {
height: 20px;
width: 20px;
margin-top: 15px;
padding-left:9px;
padding-right: 4px;
fill: gray;
}
</style>