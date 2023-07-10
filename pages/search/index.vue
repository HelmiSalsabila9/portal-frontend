<template>
    <b-container class="no-copy mt-5 mb-5">
      <b-row>
        <b-col md="12" class="mb-3">
          <!-- <h4><i class="fas fa-search mr-1"></i> PENCARIAN : <strong class="text-danger"> {{ $route.query.q.toUpperCase() }} </strong></h4> -->
          <h4><i class="fas fa-search mr-1"></i> PENCARIAN : <strong class="text-danger"> {{ $route.query.q ? $route.query.q.toUpperCase() : '' }} </strong></h4>
        </b-col>
        <b-col md="4" class="mb-3" sm="12" v-for="post in posts" :key="post.id">
          <b-card :img-src="post.image" img-top tag="article" class="mb-2 h-100 rounded-lg">
            <div class="mb-2">
              <small class="text-muted mr-3"><svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-calendar-event mr-1" width="18" height="18" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M4 5m0 2a2 2 0 0 1 2 -2h12a2 2 0 0 1 2 2v12a2 2 0 0 1 -2 2h-12a2 2 0 0 1 -2 -2z"></path><path d="M16 3l0 4"></path><path d="M8 3l0 4"></path><path d="M4 11l16 0"></path><path d="M8 15h2v2h-2z"></path></svg>{{ post.created_at }}</small>
            </div>
            <h5>
              <nuxt-link :to="{name: 'post-slug', params: {slug: post.slug}}">{{ post.title }}</nuxt-link>
            </h5>
            <b-card-text>
              {{ post.description.substr(0, 55) }}...
            </b-card-text>
            <b-card-text>
              <small class="text-muted mr-3"><svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-user mr-1" width="18" height="18" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M12 7m-4 0a4 4 0 1 0 8 0a4 4 0 1 0 -8 0"></path><path d="M6 21v-2a4 4 0 0 1 4 -4h4a4 4 0 0 1 4 4v2"></path></svg>{{ post.user.name }} - Dilihat {{ post.views }} kali</small>
            </b-card-text>
          </b-card>
        </b-col>
      </b-row>
      <b-row class="mt-4 justify-content-center">
        <b-pagination v-model="pagination.current_page" :total-rows="pagination.total" :per-page="pagination.per_page"
          @input="changePage" aria-controls="my-table">
        </b-pagination>
      </b-row>
    </b-container>
</template>
  
<script>
    export default {
      //meta
      head() {
        return {
          title: 'Pencarian - portal.helmisalsabila.com',
          meta: [{
              hid: 'og:title',
              name: 'og:title',
              content: 'portal.helmisalsabila.com'
            },
            {
              hid: 'og:site_name',
              name: 'og:site_name',
              content: 'portal.helmisalsabila.com'
            },
            {
              hid: 'og:image',
              name: 'og:image',
              content: 'https://i.imgur.com/XkrfJfo.png'
            },
          ]
        }
      },
  
      //watch query URL
      watchQuery: ["q", "page"],
  
      async asyncData({ $axios, query }) {
  
        //fetching posts
        const posts = await $axios.$get(`/api/web/posts?q=${query.q}&page=${parseInt(query.page)}`)
  
        return {
          'posts': posts.data.data,
          'pagination': posts.data
        }
      },
  
      methods: {
        //change page pagination
        changePage(page) {
          this.$router.push({
            path: this.$route.path,
            query: {
              q: this.$route.query.q,
              page: page
            }
          });
        }
      },
    }
</script>
  
<style>
  .no-select {
    user-select: none;
  }
</style>