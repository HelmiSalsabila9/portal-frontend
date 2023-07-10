<template>
  <div>
    <b-jumbotron class="p-3 rounded-0 mb-0">
      <b-container class="no-copy">
        <b-row class="mt-2">
            <b-col md="2" class="text-center">
              <a href="/"><b-img src="https://i.imgur.com/XkrfJfo.png" rounded="" width="250"></b-img></a>
            </b-col>
            <b-col md="10">
              <p class="float-md-right text-center align-text-bottom mt-3">Portal Edukasi & Informasi Masa Kini <br><small>portal.helmisalsabila.com</small></p>
              
            </b-col>
          </b-row>
      </b-container>
    </b-jumbotron>

    <b-navbar toggleable="lg" type="dark" class="bg-navbar">
      <b-container>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

        <b-collapse id="nav-collapse" is-nav>
          <b-navbar-nav>
            <b-nav-item v-for="menu in menus" :key="menu.id" :to="menu.url">{{ menu.name.toUpperCase() }}</b-nav-item>
          </b-navbar-nav>

          <!-- Right aligned nav items -->
          <b-navbar-nav class="ml-auto">
            <b-form-input v-model="search" @keypress.enter="searchData" size="sm" class="mr-sm-2 border-0" placeholder="Tulis kata kunci...">
            </b-form-input>
            <b-button @click="searchData" size="sm" class="my-2 my-sm-0" variant="primary">CARI</b-button>
          </b-navbar-nav>
        </b-collapse>
      </b-container>
    </b-navbar>
  </div>
</template>

<script>
  export default {

    //data function
    data() {
      return {
        //state menus
        menus: [],

        //state search
        search: ''
      }
    },

    async fetch() {

      //fething menus on Rest API
      await this.$axios.get('/api/web/menus')
        .then(response => {

          //assign response to state "menus"
          this.menus = response.data.data
        })
    },

    methods: {
      searchData() {
        this.$router.push({
          name: 'search',
          query: {
            q: this.search
          }
        });
      }
    }

  }
</script>

<style>
  
  .no-select {
    user-select: none;
  }

</style>