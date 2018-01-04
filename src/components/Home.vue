<template>
  <div>
    <h3 class="title">
      Welcome to The Lead Generation Automation Tool
    </h3>
    <v-container fluid grid-list-md>
      <v-text-field light solo prepend-icon="search" v-model="textSearch" placeholder="Search" style="max-width: 600px; min-width: 128px"></v-text-field>
      <v-layout row wrap>
        <v-flex d-flex xs12 sm6 md4 v-for="item in projectsFilter" v-bind:todo="item" :key="item.id">
          <router-link :to="`/plans/${item._id}`" style="color: white;text-decoration: none;">
            <v-card color="indigo" dark>
              <v-card-title primary class="title">{{ item.name }}</v-card-title>
              <v-card-text v-text="lorem">
              </v-card-text>
            </v-card>
          </router-link>
        </v-flex>
      </v-layout>
    </v-container>
  </div>
</template>



<script>
  import axios from 'axios'
  import projectdata from '../mock/projects.json'
  export default {
    name: 'Hello',
    data: function() {
      return {
        textSearch: "",
        projects: projectdata,
        lorem: `Lorem ipsum dolor sit amet, mel at clita quando.`
      }
    },
    computed: {
      projectsFilter: function() {
        var textSearch = this.textSearch;
        return this.projects.filter(function(projects) {
          return projects.name.toLowerCase().indexOf(textSearch.toLowerCase()) !== -1;
        });
      }
    },
    //call when apis are done
    created: function() {
      var that = this
      axios.get('http://localhost:64482/api/applications')
        .then(function(response) {
          that.projects = response.data;
        })
        .catch(function(error) {
          console.log(error);
        });
    }
  }
</script>
