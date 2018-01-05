<template>
  <div>
  <h3 class="title">
  Test Plans:
  </h3>
  <v-data-table
    :headers="headers"
    :items="plans"
    hide-actions
    item-key="_id"
  >
    <template slot="items" slot-scope="props">
      <tr @click="props.expanded = !props.expanded">
        <td>{{ props.item.name }}</td>
        <td class="text-xs-right">{{ props.item.status }}</td>
        <td class="text-xs-right">{{ props.item.type }}</td>
        <td class="text-xs-right">{{ props.item.jira_id }}</td>
        <td class="text-xs-right"><v-btn @click.stop="dialog = !dialog"><v-icon class="fas fa-edit"></v-icon></v-btn></td>
        <td class="text-xs-right"><v-btn @click.stop="dialog = !dialog"><v-icon class="fas fa-trash-alt"></v-icon></v-btn></td>
      </tr>
    </template>
    <template slot="expand" slot-scope="props">
      <v-data-table
      :headers="headers"
      :items="props.item.cases"
      hide-actions
      item-key="name"
       style="padding: 12px;"
      >
    <template slot="items" slot-scope="props">
      <tr>
        <td>{{ props.item.name }}</td>
        <td class="text-xs-right">{{ props.item.status }}</td>
        <td class="text-xs-right">{{ props.item.type }}</td>
        <td class="text-xs-right">{{ props.item.jira_id }}</td>
        <td class="text-xs-right"><v-btn @click.stop="dialog = !dialog"><v-icon class="fas fa-edit"></v-icon></v-btn></td>
        <td class="text-xs-right"><v-btn @click.stop="dialog = !dialog"><v-icon class="fas fa-trash-alt"></v-icon></v-btn></td>
      </tr>
    </template>
      </v-data-table>
    </template>
  </v-data-table>
    <v-dialog v-model="dialog" width="800px">
      <v-card>
        <v-card-title
          class="grey lighten-4 py-4 title"
        >
          Create contact
        </v-card-title>
        <v-container grid-list-sm class="pa-4">
          <v-layout row wrap>
            <v-flex xs12 align-center justify-space-between>
              <v-layout align-center>
                <v-avatar size="40px" class="mr-3">
                  <img
                    src="//ssl.gstatic.com/s2/oz/images/sge/grey_silhouette.png"
                    alt=""
                  >
                </v-avatar>
                <v-text-field
                  placeholder="Name"
                ></v-text-field>
              </v-layout>
            </v-flex>
            <v-flex xs6>
              <v-text-field
                prepend-icon="business"
                placeholder="Company"
              ></v-text-field>
            </v-flex>
            <v-flex xs6>
              <v-text-field
                placeholder="Job title"
              ></v-text-field>
            </v-flex>
            <v-flex xs12>
              <v-text-field
                prepend-icon="mail"
                placeholder="Email"
              ></v-text-field>
            </v-flex>
            <v-flex xs12>
              <v-text-field
                type="tel"
                prepend-icon="phone"
                placeholder="(000) 000 - 0000"
                mask="phone"
              ></v-text-field>
            </v-flex>
            <v-flex xs12>
              <v-text-field
                prepend-icon="notes"
                placeholder="Notes"
              ></v-text-field>
            </v-flex>
          </v-layout>
        </v-container>
        <v-card-actions>
          <v-btn flat color="primary">More</v-btn>
          <v-spacer></v-spacer>
          <v-btn flat color="primary" @click="dialog = false">Cancel</v-btn>
          <v-btn flat @click="dialog = false">Save</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
  import axios from 'axios'
  import plansdata from '../mock/plans.json'
  export default {
    name: 'Plans',
    data: function() {
      return {
        dialog: false,
        textSearch: "",
        plans: plansdata,
        headers: [{
            text: 'Name',
            align: 'left',
            sortable: true,
            value: 'name'
          },
          {
            text: 'Status',
            value: 'status'
          },
          {
            text: 'Type',
            value: 'type'
          },
          {
            text: 'Jira ID',
            value: 'jira_id'
          }
        ]
      }
    },
    created() {
     // this.fetchData()
    },
    watch: {
      '$route': 'fetchData'
    },
    /*computed: {
      plans: function() {
        var textSearch = this.textSearch;
        return this.plans.filter(function(plans) {
          console.log(plans);
          return plans;
        });
      }
    },*/
    methods: {
      fetchData() {
        var that = this
        axios.get('http://localhost:64482/api/applications/' + this.$route.params.id + '/Nodes/')
          .then((resp) => {
            // this.suites = resp.data[1].children;
          })
          .catch((err) => {
            console.log(err)
          })
      }
    }
  }
</script>