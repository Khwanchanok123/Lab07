<script setup>
import news from "../json/news.json";
</script>

<template>
  <header>
    <div style="padding-top 1.5em;padding-bottom: 1.5em; background-color: #66BB6A">
      <h1 class="m-0"><center>Welcome!</center></h1>
      <h2 class="m-0"><center>ระบบลงทะเบียนเรียนออนไลน์</center></h2>
      <h3 class="m-0"><center><font color=“#311b92”>สาขาวิทยาการคอมพิวเตอร์ [Computer Science]</font></center></h3>
    </div>
    <hr />
  </header>
  <body style = "background-color: #C8E6C9">
    <h3><center>!! ข่าวสารล่าสุด !!</center></h3>
    <hr />
    <article>
      <table>
        <tr>
          <th><font color=“#311b92”>วันที่</font></th>
          <th><font color=“#311b92”>หัวข้อข่าว</font></th>
        </tr>

        <tr v-for="news_content in news" :key="news_content.newsId">
          <td style="text-align: left">{{ news_content.News_Date }}</td>
          <pre class="tab2"><font size="4"><a :href="news_content.News_links"> >> {{ news_content.News_Title }}</a></font></pre>
        </tr>
      </table>
    </article>
  </body>
</template>
<style>
.content {
  margin-top: 1em;
  margin-bottom: 1em;
}
.m-0 {
  margin: unset;
}
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
