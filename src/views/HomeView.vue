<script>
import news from "../json/news.json";
export default {
  data() {
    return {
      news: news
    };
  },
  methods: {
    truncateWords(text, wordLimit) {
      const words = text.split(" ");
      if (words.length <= wordLimit) {
        return text;
      }
      return words.slice(0, wordLimit).join(" ") + "...";
    }
  }
};
</script>

<template><v-app style = "background-color: #C8E6C9">
  <v-main style="--v-layout-left: 50px; --v-layout-right: 50px; --v-layout-top: 60px; --v-layout-bottom: 0px;">
  <header>
    <div :style="{'background-image':'url(https://static.vecteezy.com/system/resources/previews/002/757/595/original/cyber-circuit-future-technology-concept-background-free-vector.jpg)'}" style="width=100%; height=100%">
    <div style="padding-top 1.5em;padding-bottom: 1.5em;">
      <h1 class="m-0"><center><font color=#E8EAF6>Welcome!</font></center></h1>
      <h2 class="m-0"><center><font color=#EFEBE9>ระบบลงทะเบียนเรียนออนไลน์</font></center></h2>
      <h3 class="m-0"><center><font color=#B2EBF2>สาขาวิทยาการคอมพิวเตอร์ [Computer Science]</font></center></h3>
    </div>
    </div>
    <hr />
  </header>
  <body style = "background-color: #C8E6C9">
    <br>
    <h3><center><font color=“#311b92”>!! ข่าวสารล่าสุด !!</font></center></h3>
    <br>
    <hr />
  
      <v-container>
        <v-row>
          <v-col cols="6" sm="6" md="4" v-for="news_content in news" :key="news_content.newsId">
            <v-card class="mx-4" max-width="400">
              <v-img class="align-end text-white" height="200" :src="news_content.News_Picture" cover />
              <v-card-title>{{ news_content.News_Title }}</v-card-title>
              <v-card-subtitle class="pt-2">วันที่:
                {{ news_content.News_Date}}
              </v-card-subtitle>
              <v-card-text>
                <div>{{truncateWords( news_content.News_Detail , 60) }}</div>
              </v-card-text>
              <v-card-actions class="justify-end">
                <v-btn color="red"><a :href="news_content.News_links">Linkเพิ่มเติม</a></v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>

  </body>
</v-main>
</v-app>

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
