<template><v-app style = "background-color: #C8E6C9">
  <v-main
        style="
          --v-layout-left: 50px;
          --v-layout-right: 50px;
          --v-layout-top: 60px;
          --v-layout-bottom: 0px;
        "
        ><v-card-title primary-title> ค้นหาวิชาที่ลงทะเบียน </v-card-title>
    <v-form @submit.prevent="addToBasket">
      <v-text-field
        type="text"
        v-model="courseID"
        placeholder="รหัสวิชา"
      ></v-text-field><v-spacer></v-spacer>
      <v-spacer></v-spacer><v-btn type="submit">ลงทะเบียน</v-btn><v-spacer></v-spacer><v-spacer></v-spacer>
    </v-form>

    <article v-if="(x = courseData.find((elem) => elem.course_id == courseID))">
      <div class="border background-color: #E6EE9C">
        <div style="background-color: #E6EE9C">
        
        <p>
          <b>รหัสวิชา : </b> <span>{{ x.course_id }}</span>
        </p>
        <br>
        <p>
          <b>ชื่อวิชา : </b> <span>{{ x.course_name }}</span>
        </p>
        <br>
        <p>
          <b>หน่วยกิต : </b><span>{{ x.credit }}</span>
        </p>
      </div>
      </div>
    </article>
    <article v-else>
      <br>
      <p>ไม่พบผลการค้นหา</p>
    </article>

    <hr />
    <div align="center">
      <br>
      <h3><font color=“#311b92”>ตะกร้า</font></h3>
      <br>
      <table>
        <thead>
          <th>รหัสวิชา</th>
          <th>ชื่อวิชา</th>
          <th>หน่วยกิต</th>
        </thead>
        <br>
        <tbody>
          <tr v-for="(course, index) in courseInfo" :key="index">
            <td>{{ course.course_id }}</td>
            <td>{{ course.course_name }}</td>
            <td>{{ course.credit }}</td>
            <td><v-btn color = "error"><button @click="removeFromBasket(index)">ลบ</button></v-btn></td>
          </tr>
        </tbody>
      </table>
      <br>
      <v-btn color = "success">
      <button @click="enrollCourse">ยืนยันการลงทะเบียน</button>
    </v-btn>
    </div>
</v-main>
</v-app>
</template>
<script setup>
import { ref } from "vue";
import courseData from "../json/cs_courses.json";
import { useEnrollment } from "../stores/useEnrollment";

const enrollment = useEnrollment();

const courseID = ref("");
let courseInfo = ref([]);
function addToBasket() {
  const data = courseData.find((elem) => elem.course_id == courseID.value);
  //console.log(data);
  if (data) {
    courseInfo.value.push(data);
    courseID.value = "";
  } else {
    alert("โปรดกรอกรหัสวิชาที่ถูกต้อง");
  }
}
function removeFromBasket(course_key) {
  if (confirm("ต้องการลบรายวิชาหรือไม่?")) {
    courseInfo.value.pop(course_key);
  }
}
function enrollCourse() {
  if (courseInfo.value.length != 0) {
    courseInfo.value.forEach((subject) => {
      enrollment.storeState(subject);
    });
    console.log(enrollment.getState);
    courseInfo.value = [];
    alert("ลงทะเบียนแล้ว โปรดไปที่หน้าวิชาที่ลงทะเบียน");
  } else {
    alert("โปรดเลือกวิชาก่อนทำการลงทะเบียน");
  }
}
</script>
<style scoped>
.border {
  margin: 20px auto;
  padding: 1em;
  border: 3px solid #2E7D32
  border-radius 10px;
  border-color: coral;
  ;
}
</style>
