<template>
  <div>
  <div>
  <v-card>
    <v-toolbar color="blue" dark flat>
      <v-text-field
        class="mx-4"
        flat
        hide-details
        label="Anime Name"
        prepend-inner-icon="mdi-magnify"
        solo-inverted
        v-model="textSearch">
         </v-text-field>

         <v-btn depressed large color="danger" @click="searchData()">Search</v-btn>
    </v-toolbar>
  </v-card>
  </div>
  <template>
  <v-card
    class="mx-auto"
  >
    <v-container>
      <v-row dense>
        <v-col cols="12" v-for="data in List" :key="data.mal_id">
          <v-card
            color="#385F73"
            dark
          >
          <v-img
      :src="data.image_url"
      height="400px"
    ></v-img>
            <v-card-title class="headline">
              {{data.title}}
            </v-card-title>

            
            
            <v-card-actions>
             <nuxt-link :to="{name:'anime-detail',
              params: { title:data.title, 
                        img:data.image_url ,
                        info:data.synopsis,
                        type:data.type,
                        ep:data.episodes,
                        sc:data.score,
                        str:data.start_date,
                        end:data.end_date
              }} ">
              <v-btn depressed large color="pink" text>Details</v-btn></nuxt-link>
            </v-card-actions>
          </v-card>
        </v-col>

        <v-col
          v-for="(item, i) in items"
          :key="i"
          cols="12"
        >
          <v-card
            :color="item.color"
            dark
          >
            <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                <v-card-title
                  class="headline"
                  v-text="item.title"
                ></v-card-title>

                <v-card-subtitle v-text="item.artist"></v-card-subtitle>

                <v-card-action>
                  <v-btn
                    v-if="item.artist === 'Ellie Goulding'"
                    class="ml-2 mt-3"
                    fab
                    icon
                    height="40px"
                    right
                    width="40px"
                  >
                    <v-icon>mdi-play</v-icon>
                  </v-btn>

                  <v-btn
                    v-else
                    class="ml-2 mt-5"
                    outlined
                    rounded
                    small
                  >
                    START RADIO
                  </v-btn>
                </v-card-action>
              </div>

              <v-avatar
                class="ma-3"
                size="125"
                tile
              >
                <v-img :src="item.src"></v-img>
              </v-avatar>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-card>
</template>
  <!--{{List}}-->
  <b-card-group columns>
  <b-card
  v-for="data in List" :key="data.mal_id"
    :title="data.title"
    :img-src="data.image_url"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem;"
    class="mb-2"
  >
    <!--<b-card-text>
      {{data.synopsis}}
    </b-card-text>-->
   
  </b-card>
  </b-card-group>
  </div>
</template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      List: null,
      textSearch: "",
    };
  },
  methods: {
    searchData() {
      axios
        .get("https://api.jikan.moe/v3/search/anime?q=" +this.textSearch+"&limit=15")
        .then((response) => {
          this.List = response.data.results;
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>
<style>
</style>