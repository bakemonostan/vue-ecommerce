<template>
  <header id="home">
    <RouterLink to="/" class="logo">IChair</RouterLink>
    <ul class="nav">
      <li v-for="item in navs" :key="item.id" @click="handleNavActive(item.id)">
        <RouterLink
          :to="item.link"
          v-if="item.name === 'Home'"
          :class="{ active: item.active }"
        >
          <i class="bi bi-house-door-fill"></i>
        </RouterLink>
        <RouterLink v-else :to="item.link" :class="{ active: item.active }">{{
          item.name
        }}</RouterLink>
      </li>
    </ul>
    <div class="features">
        <CartButton/>
    </div>
  </header>
</template>

<script setup>
import { navsData } from "@/data/data";
import { ref } from "vue";
import CartButton from "./CartButton.vue";
const navs = ref(navsData);

const handleNavActive = (id) => {
  navs.value.forEach((item) => {
    if (item.id === id) {
      item.active = true;
    } else {
      item.active = false;
    }
  });
};
</script>

<style scoped>
header {
  position: relative;
  width: 95%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 30px 100px 30px 200px;
  z-index: 1100;
}

.logo {
  font-size: 35px;
  color: #fff;
  letter-spacing: 2px;
  font-weight: 800;
}
.nav {
  display: flex;
}

.nav li a {
  color: #ffffff;
  text-decoration: none;
  font-weight: 600;
  letter-spacing: 2px;
  cursor: pointer;
  transition: 0.3s;
}
.nav li {
  list-style: none;
  margin: 0 10px;
}

.nav li:hover a,
.nav li a.active {
  color: var(--primary);
}
.features {
  display: flex;
  align-items: center;
  gap: 10px;
}
@media (max-width: 768px) {
  header {
    padding: 10px 50px;
  }
  .nav {
    display: none;
  }
}
</style>
