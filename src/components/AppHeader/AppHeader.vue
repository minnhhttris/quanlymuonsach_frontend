<template>
    <nav class="navbar bg-body-tertiary">
      <div class="container-fluid">
        <div class="infoUser">
          <div v-if="isUserLoggedIn()" class="contentInfo">
            <span class="nameUser">
              {{ username }}
            </span>
            <img :src="imageUser" class="imageUser" alt="noImage" />
          </div>
          <div v-else>
            <router-link to="/login" class="text-decoration-none">
              <button class="btnLogin">Đăng nhập</button>
            </router-link>
          </div>
        </div>
      </div>
    </nav>
  </template>
  
  <script setup>
  const isUserLoggedIn = () => {
    return localStorage.getItem("isLoginDG") === "true";
  };
  const username = localStorage.getItem("TenDG");
  const Avatar = localStorage.getItem("AvatarDG");
  const imageUser = `http://localhost:3000/${Avatar}`;
  </script>
  
  <style lang="scss" scoped>
  @import "AppHeader.scss";
  </style>