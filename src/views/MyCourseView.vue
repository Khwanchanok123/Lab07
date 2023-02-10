<template><v-app style = "background-color: #C8E6C9">
  <v-main
  style="
    --v-layout-left: 10px;
    --v-layout-right: 10px;
    --v-layout-top: 60px;
    --v-layout-bottom: 0px;
  "
>
  <div style="background-color: #66BB6A">
    <h3><center>วิชาที่ลงทะเบียนทั้งหมด</center></h3>
  </div>
  <br>
  <v-form @submit.prevent="addToBasket">
    <v-table align="center">
      <thead align="center">
        <tr>
          <th class="text-left"><font color=“#311b92”>รหัสวิชา</font></th>
          <th class="text-left"><font color=“#311b92”><pre class ="tab4">                                          ชื่อวิชา</pre></font></th>
          <th class="text-left"><font color=“#311b92”>หน่วยกิต</font></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(subject, index) in myEnrollment" :key="index">
          <td>{{ subject.course_id }}</td>
          <td><pre class ="tab2">                                    {{ subject.course_name }}</pre></td>
          <td>{{ subject.credit }}</td>
          <td><v-btn color = "error"><button @click="removeFromBasket(index)">ลบ</button></v-btn></td>
        </tr>
      </tbody>
    </v-table>
  </v-form>
  </v-main>
</v-app>
</template>
<script setup>
import { useEnrollment } from "../stores/useEnrollment";
const enrollmentList = useEnrollment();
const myEnrollment = enrollmentList.getState;
function removeFromBasket(subject_key) {
  if (confirm("ต้องการถอนรายวิชาหรือไม่?") === true) {
    enrollmentList.removeState(subject_key);
  }
}

</script>
<style>
.tab1 {
    tab-size: 2;
}

.tab2 {
    tab-size: 4;
}

.tab4 {
    tab-size: 8;
}
</style>
