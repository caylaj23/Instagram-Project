<script setup>
import { RouterView } from "vue-router";
import { useRouter } from "vue-router";
const router = useRouter();


</script>

<template>
    <div class="nav-bar">
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/NewPost">New Post</RouterLink>
</div>
  <body>
    <header>
      <div class="insta-container">
        <div class="instagram-text">
          <img src="./assets/instagram.jpeg" />
        </div>
      </div>
    </header>
  </body>
  <RouterView></RouterView>
</template>

<style scoped>

.nav-bar {
    display: flex;
    justify-content:space-between;
}


.instagram-text {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.new-post {
  text-decoration: underline;
  color: blue;
  display: flex;
  justify-content: end;
  font-size: larger;
}
</style>
