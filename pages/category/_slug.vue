<template>
    <b-container class="no-copy mt-5 mb-5">
      <b-row>
        <b-col md="12" class="mb-3">
          <h4>KATEGORI : <strong class="text-danger">{{ category.name.toUpperCase() }}</strong></h4>
        </b-col>
        <b-col md="4" class="mb-3" sm="12" v-for="post in posts" :key="post.id">
          <b-card :img-src="post.image" img-top tag="article" class="mb-2 h-100 rounded-lg">
            <div class="mb-2">
              <small class="text-muted mr-3"><svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-calendar-event mr-1" width="18" height="18" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M4 5m0 2a2 2 0 0 1 2 -2h12a2 2 0 0 1 2 2v12a2 2 0 0 1 -2 2h-12a2 2 0 0 1 -2 -2z"></path><path d="M16 3l0 4"></path><path d="M8 3l0 4"></path><path d="M4 11l16 0"></path><path d="M8 15h2v2h-2z"></path></svg>{{ post.created_at }}</small>
            </div>
            <h5>
              <nuxt-link :to="{name: 'post-slug', params: {slug: post.slug}}" class="text-bold">{{ post.title }}</nuxt-link>
            </h5>
            <b-card-text>
              {{ post.description.substr(0, 55) }}...
            </b-card-text>
            <b-card-text>
              <small class="text-muted mr-3"><i class="fa fa-eye mr-1"></i>{{ post.views }}x Dilihat</small>
              <small class="text-muted"><i class="fa fa-comments mr-1"></i>{{ post.comments.length }} Komentar</small>
            </b-card-text>
          </b-card>
        </b-col>
      </b-row>
    </b-container>
</template>
  
<script>
    export default {
  
      //meta
      head() {
        return {
          title: this.category.name + ' - portal.helmisalsabila.com',
          meta: [{
              hid: 'og:title',
              name: 'og:title',
              content: this.category.name
            },
            {
              hid: 'og:site_name',
              name: 'og:site_name',
              content: this.category.name
            },
            {
              hid: 'og:image',
              name: 'og:image',
              content: this.category.image
            },
          ]
        }
      },
  
      async asyncData({params, $axios}) {
  
        //fetching posts by category
        const category = await $axios.$get(`/api/web/categories/${params.slug}`)
  
        return {
          'category': category.data,
          'posts': category.data.posts
        }
      }
  
    }
</script>
  
<style>
  
  .no-select {
    user-select: none;
  }
  
</style>