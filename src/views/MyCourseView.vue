<template>
  <div style="background-color: #66BB6A">
    <h3><center>วิชาที่ลงทะเบียนทั้งหมด</center></h3>
  </div>
  <hr />
    <table align="center">
      <thead align="center">
        <th><font color=“#311b92”>รหัสวิชา</font></th>
        <th><font color=“#311b92”>ชื่อวิชา</font></th>
      </thead>
      <tbody>
        <tr v-for="(subject, index) in myEnrollment" :key="index" >
          <td style="text-align: left">{{ subject.course_id }}</td>
          <pre class="tab2"><font size="4">      {{ subject.course_name }}</font> </pre>
        </tr>
      </tbody>
    </table>
</template>
<script>
import { useEnrollment } from "../stores/useEnrollment";

const enrollmentList = useEnrollment();

const myEnrollment = enrollmentList.getState;
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
