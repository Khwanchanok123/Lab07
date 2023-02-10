<script setup>
//import "@/assets/css/pico.min.css";
import { RouterLink, RouterView } from "vue-router";
</script>

<template><v-app>
  <main class="container">
    <header class="header-margin"> 
      <v-app-bar color="#388E3C" dense dark>
        <v-spacer></v-spacer> <v-spacer></v-spacer>
        <v-btn small elevation="" color="error">
          <RouterLink to="/"><font size="3.5">หน้าแรก</font></RouterLink></v-btn
        > <v-spacer></v-spacer>
        <v-btn small elevation="" >
          <RouterLink to="/courses"><font size="3.5">รายวิชา</font></RouterLink></v-btn
        > <v-spacer></v-spacer>
        <v-btn small elevation="" color="">
          <RouterLink to="/enrollments"><font size="3.5">ลงทะเบียนเรียน</font></RouterLink></v-btn
        > <v-spacer></v-spacer>
        <v-btn small elevation="" color="">
          <RouterLink to="/mycourse"><font size="3.5">วิชาที่ลงทะเบียน</font></RouterLink></v-btn
        ><v-spacer></v-spacer> <v-spacer></v-spacer>
      </v-app-bar>
    </header>

    <RouterView />
  </main>
</v-app>
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
