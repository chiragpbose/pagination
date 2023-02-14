<template>
  <div> <Cards v-bind:articles="articles"/></div>
</template>

<script lang="ts">
import axios from "axios";
import Cards from "./Cards.vue";

export default {
  components:{
    Cards
  },
  name: "IndexPage",
  data() {
    return { articles: [] };
  },
  async created() {
    const res = await axios.get(
      "https://newsapi.org/v2/everything?sources=bbc-news&apiKey=70905943afe0477ab21103fdbb396454"
    );
    const dat = await res.data;

    this.articles = dat.articles;
    //console.log(this.articles);
  },
};
</script>
