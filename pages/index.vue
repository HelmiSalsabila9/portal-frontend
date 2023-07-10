<template>
  <div>
    <!-- slider -->
    <Slider />

    <b-container class="no-copy mt-5">
      <b-col md="12" class="mb-3">
        <h6 class="text-dark text-bold"><svg viewBox="0 0 24 24" width="20" height="20" aria-hidden="true" class="mr-1" xmlns="http://www.w3.org/2000/svg"><title/><path d="M22.984.638a.5.5,0,0,0-.718-.559L1.783,10.819a1.461,1.461,0,0,0-.1,2.527h0l4.56,2.882a.25.25,0,0,0,.3-.024L18.7,5.336a.249.249,0,0,1,.361.342L9.346,17.864a.25.25,0,0,0,.062.367L15.84,22.3a1.454,1.454,0,0,0,2.19-.895Z"/><path d="M7.885,19.182a.251.251,0,0,0-.385.211c0,1.056,0,3.585,0,3.585a1,1,0,0,0,1.707.707l2.018-2.017a.251.251,0,0,0-.043-.388Z"/></svg> ARTIKEL TERBARU</h6>
      </b-col>  
    </b-container>
    <b-container class="no-copy mt-3 mb-5">
      <b-row>
        <b-col md="8" sm="12">
          <b-card no-body class="border-0 rounded-lg shadow-sm mb-3" v-for="post in posts" :key="post.id">
            <b-row class="g-0">
              <b-col md="4">
                <b-img :src="post.image" class="w-100 img-post h-100 object-fit-cover" rounded="left"></b-img>
              </b-col>
              <b-col md="8">
                <b-card-body>
                  <h5>
                    <nuxt-link :to="{name: 'post-slug', params: {slug: post.slug}}" class="text-bold">{{ post.title }}</nuxt-link>
                  </h5>
                  <b-card-text> {{ post.description.substr(0, 55) }}...</b-card-text>
                  <b-card-text>
                    <small class="text-muted mr-3"><svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-user mr-1" width="18" height="18" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M12 7m-4 0a4 4 0 1 0 8 0a4 4 0 1 0 -8 0"></path><path d="M6 21v-2a4 4 0 0 1 4 -4h4a4 4 0 0 1 4 4v2"></path></svg>{{ post.user.name }}</small>

                    <small class="text-muted mr-3"><svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-calendar-event mr-1" width="18" height="18" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M4 5m0 2a2 2 0 0 1 2 -2h12a2 2 0 0 1 2 2v12a2 2 0 0 1 -2 2h-12a2 2 0 0 1 -2 -2z"></path><path d="M16 3l0 4"></path><path d="M8 3l0 4"></path><path d="M4 11l16 0"></path><path d="M8 15h2v2h-2z"></path></svg>{{ post.created_at }} </small>

                    <small class="text-muted mr-3"><i class="fa fa-comments mr-1"></i> {{ post.comments.length }} Komentar</small>
                    <!-- <small class="text-muted mr-3"><i class="fa fa-eye mr-1"></i> {{ post.views }} Dilihat</small> -->
                  </b-card-text>
                </b-card-body>
              </b-col>
            </b-row>
          </b-card>
          <b-row class="mt-5">
            <b-col md="12" class="text-center">
              <nuxt-link :to="{name: 'post'}" class="btn btn-md btn-info rounded shadow-sm">LIHAT LEBIH BANYAK</nuxt-link>
            </b-col>
          </b-row>
        </b-col>
        <b-col md="4" sm="12">
          <b-card no-body class="border-0 rounded-lg shadow-sm">
            <b-card-body>
              <h6 class="text-bold"><svg data-name="Layer 2" aria-hidden="true" width="20" height="20" class="mr-1" id="e73e2821-510d-456e-b3bd-9363037e93e3" viewBox="0 0 35 35" xmlns="http://www.w3.org/2000/svg"><path d="M11.933,15.055H3.479A3.232,3.232,0,0,1,.25,11.827V3.478A3.232,3.232,0,0,1,3.479.25h8.454a3.232,3.232,0,0,1,3.228,3.228v8.349A3.232,3.232,0,0,1,11.933,15.055ZM3.479,2.75a.73.73,0,0,0-.729.728v8.349a.73.73,0,0,0,.729.728h8.454a.729.729,0,0,0,.728-.728V3.478a.729.729,0,0,0-.728-.728Z"/><path d="M11.974,34.75H3.52A3.233,3.233,0,0,1,.291,31.521V23.173A3.232,3.232,0,0,1,3.52,19.945h8.454A3.232,3.232,0,0,1,15.2,23.173v8.348A3.232,3.232,0,0,1,11.974,34.75ZM3.52,22.445a.73.73,0,0,0-.729.728v8.348a.73.73,0,0,0,.729.729h8.454a.73.73,0,0,0,.728-.729V23.173a.729.729,0,0,0-.728-.728Z"/><path d="M31.522,34.75H23.068a3.233,3.233,0,0,1-3.229-3.229V23.173a3.232,3.232,0,0,1,3.229-3.228h8.454a3.232,3.232,0,0,1,3.228,3.228v8.348A3.232,3.232,0,0,1,31.522,34.75Zm-8.454-12.3a.73.73,0,0,0-.729.728v8.348a.73.73,0,0,0,.729.729h8.454a.73.73,0,0,0,.728-.729V23.173a.729.729,0,0,0-.728-.728Z"/><path d="M27.3,15.055a7.4,7.4,0,1,1,7.455-7.4A7.437,7.437,0,0,1,27.3,15.055Zm0-12.3a4.9,4.9,0,1,0,4.955,4.9A4.935,4.935,0,0,0,27.3,2.75Z"/></svg> KATEGORI</h6>
              <hr>
              <b-card no-body class="border-0 shadow-sm mb-2 rounded-lg" v-for="category in categories" :key="category.id">
                <b-card-body class="p-2 fw-normal btn btn-light text-left">
                  <b-img :src="category.image" width="40" class="rounded mr-1"></b-img>
                  <nuxt-link :to="{name: 'category-slug', params: {slug: category.slug}}" class="text-dark"> {{ category.name }}</nuxt-link>
                </b-card-body>
              </b-card>
            </b-card-body>
          </b-card>

          <b-card no-body class="border-0 rounded-lg shadow-sm">
            <b-card-body>
              <h6 class="text-bold"><svg enable-background="new 0 0 48 48" class="mr-1" aria-hidden="true" height="22" id="Layer_1" version="1.1" viewBox="0 0 48 48" width="22" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path clip-rule="evenodd" d="M46.996,24.983v0.021c0,0.32-0.16,0.593-0.395,0.776L27.662,44.719  c-0.381,0.381-0.998,0.381-1.381,0c-0.381-0.382-0.381-1,0-1.381l18.715-18.715v-6.619c0-0.552,0.449-1,1-1c0.553,0,1,0.448,1,1  v6.973C46.996,24.979,46.996,24.98,46.996,24.983z M19.806,46.575c-0.032,0.048-0.053,0.102-0.095,0.144  c-0.197,0.196-0.457,0.287-0.715,0.281c-0.258,0.006-0.518-0.085-0.715-0.281c-0.042-0.042-0.062-0.096-0.095-0.144L1.425,29.813  c-0.048-0.032-0.101-0.053-0.144-0.095C1.084,29.521,0.995,29.262,1,29.004c-0.006-0.258,0.084-0.518,0.281-0.715  c0.043-0.042,0.096-0.062,0.144-0.095L24.221,5.398c0.183-0.234,0.455-0.395,0.775-0.395h0.021c0.002,0,0.004,0,0.006,0h4.029  c0.133-1.502,0.746-2.82,1.67-3.683l0.016,0.018c0.195-0.207,0.463-0.335,0.758-0.335c0.592,0,1.072,0.512,1.072,1.143  c0,0.375-0.18,0.691-0.441,0.899c-0.479,0.442-0.82,1.139-0.934,1.958h4.775c0.002,0,0.004,0,0.008,0h0.02  c0.32,0,0.594,0.16,0.775,0.395l5.83,5.83c0.234,0.183,0.395,0.456,0.395,0.776v0.021c0,0.002,0,0.004,0,0.006v10.945  c0,0.002,0,0.004,0,0.007v0.021c0,0.32-0.16,0.593-0.395,0.775L19.806,46.575z M40.996,12.385l-5.381-5.381h-4.213  c0.176,0.444,0.424,0.822,0.725,1.1l0,0c0.041,0.033,0.092,0.053,0.127,0.092l0.018-0.018c1.041,0.973,1.725,2.508,1.725,4.254  c0,0.042-0.01,0.079-0.012,0.12c1.197,0.691,2.012,1.97,2.012,3.452c0,2.209-1.791,4-4,4s-4-1.791-4-4  c0-2.147,1.695-3.885,3.82-3.982c-0.09-0.888-0.441-1.648-0.949-2.118c-0.041-0.033-0.092-0.053-0.129-0.092L30.723,9.83  c-0.744-0.695-1.293-1.685-1.553-2.826h-3.793l-22,22l15.619,15.619l22-22V12.385z M30.867,14.961  c0.248-0.229,0.451-0.537,0.617-0.883c-0.855,0.228-1.488,1-1.488,1.925c0,1.104,0.896,2,2,2c1.105,0,2-0.896,2-2  c0-0.473-0.17-0.901-0.445-1.244c-0.615,1.545-1.297,1.909-1.297,1.909c-0.193,0.207-0.461,0.334-0.758,0.334  c-0.592,0-1.07-0.512-1.07-1.143C30.426,15.486,30.605,15.17,30.867,14.961z M12.282,27.289c0.382-0.381,1-0.381,1.381,0  l7.049,7.049c0.381,0.381,0.381,0.999,0,1.381c-0.381,0.381-1,0.381-1.381,0l-7.049-7.049  C11.901,28.289,11.901,27.671,12.282,27.289z M16.282,23.289c0.382-0.381,1-0.381,1.381,0l7.049,7.049  c0.38,0.381,0.38,0.999,0,1.381c-0.381,0.381-1,0.381-1.381,0l-7.049-7.049C15.901,24.289,15.901,23.671,16.282,23.289z" fill-rule="evenodd"/></svg> TAG</h6>
              <hr>
              <nuxt-link :to="{name: 'tag-slug', params:{slug: tag.slug}}" class="tag-badge badge btn-light btn-sm mb-2 mr-2 shadow-sm" v-for="tag in tags" :key="tag.id" :style="{ backgroundColor: getRandomColor() }">{{ tag.name }}</nuxt-link>
            </b-card-body>
          </b-card>

        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>

  import Slider from '@/components/web/slider.vue'
  
  export default {
    data() {
      return {
        tags: []
      }
    },
    methods: {
      getRandomColor() {
        const letters = '0123456789ABCDEF';
        let color = '#';
        for (let i = 0; i < 6; i++) {
          color += letters[Math.floor(Math.random() * 16)];
        }
        return color;
      }
    },
    
    components: {
      Slider
    },

    //meta
    head() {
      return {
        title: 'PORTAL | WELCOME - portal.helmisalsabila.com',
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

    async asyncData({ $axios }) {

      //fetching posts
      const posts = await $axios.$get('/api/web/postHomepage')

      //fetching categories
      const categories = await $axios.$get('/api/web/categorySidebar')

      //fetching tags
      const tags = await $axios.$get('/api/web/tags')

      return {
        'posts': posts.data,
        'categories': categories.data,
        'tags': tags.data
      }
    }
  }
  </script>

<style>
  .no-select {
    user-select: none;
  }

  .tag-badge {
    display: inline-block;
    color: #fff;
  }

</style>