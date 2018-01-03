<template>
  <div>
    <v-container fluid grid-list-md>
      <v-layout row wrap>
        <v-flex d-flex xs12 sm6 md4 v-for="item in projectsFilter" v-bind:todo="item" :key="item.id">
          <router-link :to="`/plans/${item._id}`" class="box notification is-success">
          <v-card color="indigo" dark>
            <v-card-title primary class="title">{{ item.name }}</v-card-title>
            <v-card-text v-text="lorem">
            </v-card-text>
          </v-card>
          </router-link>
        </v-flex>
      </v-layout>
    </v-container>
    <div class="hero-body" style="padding-top: 0">
      <div class="section">
        <div class="container">
          <h1 class="title">
            Welcome to The Lead Generation Automation Tool
          </h1>
          <p class="subtitle">
            <strong>Available projects with test automation :</strong>
          </p>
          <div class="field has-addons">
            <div class="control is-expanded">
              <input class="input" v-model="textSearch" type="text" placeholder="Find a project" />
            </div>
            <div class="control">
              <a class="button is-info">Search</a>
            </div>
          </div>
        </div>
      </div>
      <div class="section">
        <div class="columns is-mobile is-multiline is-centered">
          <div class="container columns is-multiline is-centered">
            <div v-for="item in projectsFilter" v-bind:todo="item" :key="item.id" class="column is-narrow">
              <router-link :to="`/plans/${item._id}`" class="box notification is-success">
                <p class="title">{{ item.name }} </p>
                <p class="subtitle">{{ item._id }}</p>
              </router-link>
            </div>
          </div>
        </div>
      </div>
    </div>
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
        lorem: `Lorem ipsum dolor sit amet, mel at clita quando. Te sit oratio vituperatoribus, nam ad ipsum posidonium mediocritatem, explicari dissentiunt cu mea. Repudiare disputationi vim in, mollis iriure nec cu, alienum argumentum ius ad. Pri eu justo aeque torquatos.`
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
