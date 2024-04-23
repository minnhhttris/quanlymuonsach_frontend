<template>
  <nav class="navbar bg-body-tertiary">
    <div class="container-fluid">
      <div class="infoUser d-flex ml-auto">
        <div v-if="isUserLoggedIn()" class="contentInfo d-flex align-items-center">
          <router-link to="/admin/info">
            <div class="imageColumn">
              <img :src="imageUser" class="imageUser" alt="noImage" />
            </div>
          </router-link>
          <div class="infoColumn ml-1">
            <div>
              <span class="nameUser">{{ username }}</span>
            </div>
            <div>
              <span class="positionUser">{{ position }}</span>
            </div>
          </div>
        </div>
        <div v-else>
          <router-link to="/admin/login" class="text-decoration-none">
            <button class="btnLogin">Đăng nhập</button>
          </router-link>
        </div>
      </div>
    </div>
  </nav>
</template>


<script setup>
const isUserLoggedIn = () => {
  return localStorage.getItem("isLogin") === "true";
};
const username = localStorage.getItem("Username");
const Avatar = localStorage.getItem("Avatar");
const position = localStorage.getItem("Position");
const imageUser = `http://localhost:3000/${Avatar}`;
</script>

<style lang="scss" scoped>
@import "AppHeaderAdmin.scss";
</style>