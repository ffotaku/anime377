<template>
  <div>
    <v-container class="light-blue lighten-4">
      <h1 align="center">{{ this.$route.params.title }}</h1>
      <v-row class="md-6">
        <v-col class="col-md-12">
          <div align="center">
            <img :src="this.anime.img" width="300px" height="300px" />
          </div>
        </v-col>
        <v-col class="col-md-7">
          <br />
          <h3>Info: {{ this.anime.info }}</h3>
          <br />
          <h3>Rate: {{ this.anime.sc }}</h3>
          <br />
          <h3>Episodes: {{ this.anime.ep }}</h3>
          <br />
          <h3>Type: {{ this.anime.type }}</h3>
          <br />
          <h3>Start: {{ this.anime.str }}</h3>
          <br />
          <h3>End: {{ this.anime.end }}</h3>
          <br />
        </v-col>
      </v-row>
      <h1 align="center">
      </h1>
    </v-container>
  </div>
</template>
<script>
export default {
  data() {
    return {
      anime: this.$route.params,
    }
  },
}
</script>
<style>
h1 {
  color: rgb(211, 51, 211);
}
h3 {
  color: rgb(55, 24, 192);
}
</style>