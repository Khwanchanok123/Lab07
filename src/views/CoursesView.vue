<template>
  <div style="background-color: #66BB6A">
    <h3><center>รายชื่อวิชาทั้งหมด</center></h3>
  </div>
  <hr />
  <table>
    <tr>
      <th><font color=“#311b92”>รหัสวิชา</font></th>
      <th><font color=“#311b92”>ชื่อวิชา</font></th>
    </tr>
    <tr v-for="(course, index) in courses" :key="index">
      <td style="text-align: left">{{ course.course_id }}</td>
     <font size="3.5"><a @click="showAlert(index)" style="padding-left: 3em;" href="#">    {{ course.course_name }}
      </a> </font>
    </tr>
  </table>
</template>
<script>
import courses from "../json/cs_courses.json";
export default {
  methods: {
    showAlert(key) {
      // Use sweetalert2
      this.$swal({
        title: `<h4>${this.courses[key].course_name}</h4>`,
        html: [
          `<p style="margin: 0;"><strong>รหัสวิชา:</strong> ${this.courses[key].course_id}</p>
          <p style="margin: 0;"><strong>หน่วยกิต:</strong> ${this.courses[key].credit}</p>
          <p style="margin: 0;"><strong>อาจารย์ผู้สอน:</strong> unknow</p>`,
        ],
        icon: "info",
      });
    },
  },
  data() {
    return { courses };
  },
};
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
}</style>
