<template>
  <div>
    <v-container class="card-container">
      <v-layout row wrap>
        <v-flex
          xs1
          sm2
          md3
          lg4
          v-for="article in articles.slice(initial, final)"
          v-bind:key="article.title"
        >
          <v-card flat class="text-center ma-3"
            ><a class="text-link title" target="_blank" :href="article.url">{{
              article.title
            }}</a>

            <v-img :src="article.urlToImage"></v-img>
            <div class="subheading">{{ article.url }}</div>
            <div class="grey--text">20th January 2023</div>
            <a class="text-link" target="_blank" :href="article.url">
              <v-btn>View Details</v-btn>
            </a>
          </v-card>
        </v-flex>
      </v-layout>

      <v-btn @click="prevPagefn">Previous page</v-btn>
      <v-btn @click="nextPagefn">Next page</v-btn>
    </v-container>
    <h3>Current Page number: {{ currentPage+1 }}</h3>
  </div>
</template>

<script lang="ts">
export default {
  name: "Cards",
  props: ["articles"],
  data() {
    return {
      pageSize: 10,
      currentPage: 0,
      initial: 0,
      final: 10,
    };
  },
  methods: {
    nextPagefn() {
      this.currentPage++;
      this.initial = this.currentPage * 10;
      this.final = this.currentPage * 10 + 10;
    },
    prevPagefn() {
      if (this.currentPage > 0) this.currentPage--;
      this.initial = this.currentPage * 10;
      this.final = this.currentPage * 10 + 10;
    },
  },
};
</script>

<style scoped lang="scss">

a.text-link.title {
  color: white;
  &:hover {
    color: red; 
  }
}
</style>
