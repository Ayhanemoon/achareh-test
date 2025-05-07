<template>
  <header>

  <div class="header-container">
    <img alt="header__logo" class="logo" src="@/assets/logo.svg" width="70px" height="39px" />
    <nav class="header__nav">
      <RouterLink to="/">Home</RouterLink>
      <RouterLink to="/about">About</RouterLink>
    </nav>
  </div>
  </header>

  <div class="content-wrapper">
    <RouterView />
  </div>
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<style lang="scss" scoped>
.header{
  
  &-container {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: #fff;
    padding: 18px 80px;
    box-shadow: 0 .5px 2px 0 rgba(0, 0, 0, 0.15);
  }
}

.content-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: flex-start;
  padding: 33px;
  height: calc(100vh - 80px);
}
</style>