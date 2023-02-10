<script setup>
//import "@/assets/css/pico.min.css";
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
  <main class="container">
    <header class="header-margin"  style="background-color:#388E3C">
      <nav>
        <RouterLink to="/">หน้าแรก</RouterLink>
        <RouterLink to="/courses">รายวิชา</RouterLink>
        <RouterLink to="/enrollments">ลงทะเบียนเรียน</RouterLink>
        <RouterLink to="/mycourse">วิชาที่ลงทะเบียน</RouterLink>
      </nav>
    </header>

    <RouterView />
  </main>
</template>

<style scoped>
.header-margin {
  padding-top: 0.8em;
  padding-bottom: 0.8em;
}

nav > a {
  padding-left: 0.5em;
  padding-right: 0.5em;
}
</style>
