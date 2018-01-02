<template>
<section class="container" style="padding-top: 30px; padding-left: 5px;">
   <div class="columns">
      <div class="is-two-fifths" style="padding-right: 15px;">
         <nav class="panel">
            <p class="panel-heading" >
               Test Plans:
            </p>
            <div class="panel-block">
               <p class="control has-icons-left">
                  <input class="input is-small" type="text" placeholder="search">
                  <span class="icon is-small is-left">
                  <i class="fa fa-search"/>
                  </span>
               </p>
            </div>
            <p class="panel-tabs">
               <a class="is-active">all</a>
               <a>public</a>
               <a>private</a>
            </p>
            <div v-for="plan in suites" v-bind:todo="plan" :key="plan.id" >
              <a v-for="check in plan.children" class="panel-block is-active">
                <span class="panel-icon">
                  <i class="fa fa-book"/>
                </span>
                {{check.label}} 
              </a>
            </div>
            <div class="panel-block">
               <button class="button is-link is-outlined is-fullwidth">
               Add a Test Plan
               </button>
            </div>
         </nav>
      </div>
      <div>
         <table class="table">
            <thead>
               <tr>
                  <th><abbr title="Position">Pos</abbr></th>
                  <th>Team</th>
                  <th><abbr title="Played">Pld</abbr></th>
                  <th><abbr title="Won">W</abbr></th>
                  <th><abbr title="Drawn">D</abbr></th>
                  <th><abbr title="Lost">L</abbr></th>
                  <th><abbr title="Goals for">GF</abbr></th>
                  <th><abbr title="Goals against">GA</abbr></th>
                  <th><abbr title="Goal difference">GD</abbr></th>
                  <th><abbr title="Points">Pts</abbr></th>
                  <th>Qualification or relegation</th>
               </tr>
            </thead>
            <tfoot>
               <tr>
                  <th><abbr title="Position">Pos</abbr></th>
                  <th>Team</th>
                  <th><abbr title="Played">Pld</abbr></th>
                  <th><abbr title="Won">W</abbr></th>
                  <th><abbr title="Drawn">D</abbr></th>
                  <th><abbr title="Lost">L</abbr></th>
                  <th><abbr title="Goals for">GF</abbr></th>
                  <th><abbr title="Goals against">GA</abbr></th>
                  <th><abbr title="Goal difference">GD</abbr></th>
                  <th><abbr title="Points">Pts</abbr></th>
                  <th>Qualification or relegation</th>
               </tr>
            </tfoot>
            <tbody>
               <tr>
                  <th>1</th>
                  <td><a href="https://en.wikipedia.org/wiki/Leicester_City_F.C." title="Leicester City F.C.">Leicester City</a> <strong>(C)</strong>
                  </td>
                  <td>38</td>
                  <td>23</td>
                  <td>12</td>
                  <td>3</td>
                  <td>68</td>
                  <td>36</td>
                  <td>+32</td>
                  <td>81</td>
                  <td>Qualification for the <a href="https://en.wikipedia.org/wiki/2016%E2%80%9317_UEFA_Champions_League#Group_stage" title="2016–17 UEFA Champions League">Champions League group stage</a></td>
               </tr>
            </tbody>
         </table>
      </div>
   </div>
</section>


</template>
<script>
import axios from 'axios'
import VueMarkdown from 'vue-markdown'
import casesdata from '../mock/cases.json'

export default {
  name: 'Plans',
  data: function ( ) {
    return{
    suites: []
    }
  },
  created () {
    this.fetchData()
  },
  watch: {
    '$route': 'fetchData'
  },
  methods: {
    fetchData () {
      var that = this
      axios.get('http://localhost:64482/api/applications/' + this.$route.params.id + '/Nodes/')
        .then((resp) => {
          this.suites = resp.data[1].children;
        })
        .catch((err) => {
          console.log(err)
        })
    }
  }
}
</script>