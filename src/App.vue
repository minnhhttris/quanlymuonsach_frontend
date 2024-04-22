<script setup>
import "vue3-toastify/dist/index.css";
</script>
<template>
  <div>
    <component :is="$route.meta.layout">
      <router-view />
    </component>
  </div>
</template>
<style lang="scss">
:root {
  --primary: #27374D;
  --primary-alt: #526D82;
  --grey: #9DB2BF;
  --dark: #1e293b;
  --dark-alt: #334155;
  --light: #DDE6ED;
  --sidebar-width: 200px;
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Fira sans", sans-serif;
}
body {
  background: var(--light);
}
button {
  cursor: pointer;
  appearance: none;
  border: none;
  outline: none;
  background: none;
}
.app {
  display: flex;
  main {
    flex: 1 1 0;
    padding: 2rem;
    @media (max-width: 1024px) {
      padding-left: 6rem;
    }
  }
}
</style>