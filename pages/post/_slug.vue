<template>
    <b-container class="no-copy mt-5 mb-5">
      <b-row>
        <b-col md="8" sm="12">
          <b-card class="border-0 rounded-lg shadow-md mb-3">
            <h4><strong>{{ post.title }}</strong></h4>
            <hr>
            <b-img :src="post.image" class="rounded-lg w-100"></b-img>
            <b-card-text class="mt-3">
              <small class="text-muted mr-3"><svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-calendar-event mr-1" width="18" height="18" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M4 5m0 2a2 2 0 0 1 2 -2h12a2 2 0 0 1 2 2v12a2 2 0 0 1 -2 2h-12a2 2 0 0 1 -2 -2z"></path><path d="M16 3l0 4"></path><path d="M8 3l0 4"></path><path d="M4 11l16 0"></path><path d="M8 15h2v2h-2z"></path></svg>{{ post.created_at }}</small>
              <small class="text-muted mr-3"><i class="fa fa-comments mr-1"></i> {{ post.comments.length }} Komentar</small>
              <small class="text-muted mr-3"><i class="fa fa-eye mr-1"></i> {{ post.views }}x Dilihat</small>
              <small class="text-muted mr-3"><i class="fas fa-list mr-1"></i> {{ post.category.name }}</small>
              <small class="text-muted mr-3"><svg xmlns="http://www.w3.org/2000/svg" class="icon icon-tabler icon-tabler-user mr-1" width="18" height="18" viewBox="0 0 24 24" stroke-width="2" stroke="currentColor" fill="none" stroke-linecap="round" stroke-linejoin="round"><path stroke="none" d="M0 0h24v24H0z" fill="none"></path><path d="M12 7m-4 0a4 4 0 1 0 8 0a4 4 0 1 0 -8 0"></path><path d="M6 21v-2a4 4 0 0 1 4 -4h4a4 4 0 0 1 4 4v2"></path></svg>{{ post.user.name }}</small>
            </b-card-text>

            <div v-html="post.content" class="ckeditor-content"></div>

            <hr>
            <nuxt-link :to="{name: 'tag-slug', params:{slug: tag.slug}}" class="tag-badge badge badge-light btn-sm mb-2 mr-2 shadow-sm" v-for="tag in post.tags" :key="tag.id" :style="{ backgroundColor: getRandomColor() }">{{ tag.name }}</nuxt-link>
          </b-card>

          <b-card no-body>
            <b-card-header>
              <h6><strong><svg width="22" height="22" class="mr-1" aria-hidden="true" style="enable-background:new 0 0 24 24;" version="1.1" viewBox="0 0 24 24" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><g id="info"/><g id="icons"><path d="M21.7,10.2l-6.6-6C14.6,3.7,14,4.2,14,5v3c-4.7,0-8.7,2.9-10.6,6.8c-0.7,1.3-1.1,2.7-1.4,4.1   c-0.2,1,1.3,1.5,1.9,0.6C6.1,16,9.8,13.7,14,13.7V17c0,0.8,0.6,1.3,1.1,0.8l6.6-6C22.1,11.4,22.1,10.6,21.7,10.2z" id="share"/></g></svg> BAGIKAN HALAMAN 
                <hr>
                <Share />
              </strong>
            </h6>
            </b-card-header>
          </b-card>
          
          <b-card no-body>
            <b-card-body>
              <b-row>
                <b-col md="2" sm="12" class="text-center">
                  <b-img src="https://i.imgur.com/kTR7koo.png" rounded="circle" width="100" class="shadow-sm"></b-img>
                </b-col>
                <b-col md="10" sm="12">
                  <h4 class="profil-center text-bold mt-3">Helmi Salsabila <svg data-bs-toggle="tooltip" data-bs-placement="right" style="width:24px;height:24px" viewBox="0 0 24 24" data-bs-original-title="" title=""><path d="M22.5 12.5c0-1.58-.875-2.95-2.148-3.6.154-.435.238-.905.238-1.4 0-2.21-1.71-3.998-3.818-3.998-.47 0-.92.084-1.336.25C14.818 2.415 13.51 1.5 12 1.5s-2.816.917-3.437 2.25c-.415-.165-.866-.25-1.336-.25-2.11 0-3.818 1.79-3.818 4 0 .494.083.964.237 1.4-1.272.65-2.147 2.018-2.147 3.6 0 1.495.782 2.798 1.942 3.486-.02.17-.032.34-.032.514 0 2.21 1.708 4 3.818 4 .47 0 .92-.086 1.335-.25.62 1.334 1.926 2.25 3.437 2.25 1.512 0 2.818-.916 3.437-2.25.415.163.865.248 1.336.248 2.11 0 3.818-1.79 3.818-4 0-.174-.012-.344-.033-.513 1.158-.687 1.943-1.99 1.943-3.484zm-6.616-3.334l-4.334 6.5c-.145.217-.382.334-.625.334-.143 0-.288-.04-.416-.126l-.115-.094-2.415-2.415c-.293-.293-.293-.768 0-1.06s.768-.294 1.06 0l1.77 1.767 3.825-5.74c.23-.345.696-.436 1.04-.207.346.23.44.696.21 1.04z" fill="#568af5"></path></svg></h4>
                  <h6 class="profil-center text-muted">Content Creator & Founder Portal.HelmiSalsabila.com</h6>
                </b-col>
              </b-row>
              <hr>
              <h6>Suka dengan Artikelnya?</h6>
              <h6>Kamu bisa memberikan dukungan dengan berdonasi atau membagikan artikel ini ke sosial media. Terimakasih atas dukungan anda semoga Allah SWT membalas kebaikan Anda.</h6><br>
              <p class="text-center">
                <a href="https://trakteer.id/helmisalsabila" target="_blank" class="donasi-trakteer font-weight-bold text-decoration-none"><svg class="mr-1" aria-hidden="true" fill="currentColor" height="16" viewBox="0 0 24 24" width="16" xmlns="http://www.w3.org/2000/svg"><path d="M17.726 13.02 14 16H9v-1h4.065a.5.5 0 0 0 .416-.777l-.888-1.332A1.995 1.995 0 0 0 10.93 12H3a1 1 0 0 0-1 1v6a2 2 0 0 0 2 2h9.639a3 3 0 0 0 2.258-1.024L22 13l-1.452-.484a2.998 2.998 0 0 0-2.822.504zm1.532-5.63c.451-.465.73-1.108.73-1.818s-.279-1.353-.73-1.818A2.447 2.447 0 0 0 17.494 3S16.25 2.997 15 4.286C13.75 2.997 12.506 3 12.506 3a2.45 2.45 0 0 0-1.764.753c-.451.466-.73 1.108-.73 1.818s.279 1.354.73 1.818L15 12l4.258-4.61z"/></svg> TRAKTEER</a>
                <a href="https://saweria.co/helmisalsabila" target="_blank" class="donasi-saweria font-weight-bold text-decoration-none"><svg aria-hidden="true" class="mr-1" viewBox="0 0 512 512" xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor"><path d="M256 416c114.9 0 208-93.1 208-208S370.9 0 256 0 48 93.1 48 208s93.1 208 208 208zM233.8 97.4V80.6c0-9.2 7.4-16.6 16.6-16.6h11.1c9.2 0 16.6 7.4 16.6 16.6v17c15.5.8 30.5 6.1 43 15.4 5.6 4.1 6.2 12.3 1.2 17.1L306 145.6c-3.8 3.7-9.5 3.8-14 1-5.4-3.4-11.4-5.1-17.8-5.1h-38.9c-9 0-16.3 8.2-16.3 18.3 0 8.2 5 15.5 12.1 17.6l62.3 18.7c25.7 7.7 43.7 32.4 43.7 60.1 0 34-26.4 61.5-59.1 62.4v16.8c0 9.2-7.4 16.6-16.6 16.6h-11.1c-9.2 0-16.6-7.4-16.6-16.6v-17c-15.5-.8-30.5-6.1-43-15.4-5.6-4.1-6.2-12.3-1.2-17.1l16.3-15.5c3.8-3.7 9.5-3.8 14-1 5.4 3.4 11.4 5.1 17.8 5.1h38.9c9 0 16.3-8.2 16.3-18.3 0-8.2-5-15.5-12.1-17.6l-62.3-18.7c-25.7-7.7-43.7-32.4-43.7-60.1.1-34 26.4-61.5 59.1-62.4zM480 352h-32.5c-19.6 26-44.6 47.7-73 64h63.8c5.3 0 9.6 3.6 9.6 8v16c0 4.4-4.3 8-9.6 8H73.6c-5.3 0-9.6-3.6-9.6-8v-16c0-4.4 4.3-8 9.6-8h63.8c-28.4-16.3-53.3-38-73-64H32c-17.7 0-32 14.3-32 32v96c0 17.7 14.3 32 32 32h448c17.7 0 32-14.3 32-32v-96c0-17.7-14.3-32-32-32z"/></svg> SAWERIA</a>
                <a href="https://i.imgur.com/0t8jUWl.png" target="_blank" class="donasi-qris font-weight-bold text-decoration-none"><svg aria-hidden="true" fill="currentColor" class="mr-1" height="16" viewBox="0 0 24 24" width="16" xmlns="http://www.w3.org/2000/svg"><path d="M4 4h4.01V2H2v6h2V4zm0 12H2v6h6.01v-2H4v-4zm16 4h-4v2h6v-6h-2v4zM16 4h4v4h2V2h-6v2z"/><path d="M5 11h6V5H5zm2-4h2v2H7zM5 19h6v-6H5zm2-4h2v2H7zM19 5h-6v6h6zm-2 4h-2V7h2zm-3.99 4h2v2h-2zm2 2h2v2h-2zm2 2h2v2h-2zm0-4h2v2h-2z"/></svg> QRIS</a>
              </p>
            </b-card-body>
          </b-card>
  
          <b-card no-body>
            <b-card-body>
              <h6 class="text-bold"> {{ post.comments.length }} KOMENTAR</h6>
              <hr>
              <b-list-group>
                <b-list-group-item v-for="comment in post.comments" :key="comment.id" class="mb-3 shadow-sm rounded">
                  <div class="text-right">
                    <small class="text-right text-muted">{{ comment.created_at }}</small>
                  </div>
                  <b-avatar button variant="info" text="" class="align-baseline mr-1"></b-avatar>
                  <span class="font-weight-bold">{{ comment.name }}</span>
                  <hr>
                  <p>{{ comment.comment }}</p>
                </b-list-group-item>
              </b-list-group>
            </b-card-body>
          </b-card>
  
          <b-card no-body>
            <b-card-body>
              <h6 class="text-bold"><i class="fa fa-comments mr-1"></i> KEBIJAKAN KOMENTAR</h6>
              <hr>
              <h6>Saat memberikan komentar, masukan Nama Lengkap dan Email yang sesuai kemudian silahkan berikan informasi yang <strong class="text-success">POSITIF</strong> dan dilarang memberikan informasi yang <strong class="text-danger">NEGATIF.</strong></h6>
              <h6><nuxt-link :to="{name: 'kebijakan'}" class="text-primary">Lihat selengkapnya.</nuxt-link></h6>
              
            </b-card-body>
            <b-card-header>
              <b-button block v-b-toggle.accordion-2 variant="info">BERIKAN KOMENTAR</b-button>
            </b-card-header>
            <b-collapse id="accordion-2" accordion="my-accordion" role="tabpanel">
              <b-card-body>
                <b-form @submit.prevent="storeComment">
                  <b-row>
                    <b-col md="6" sm="6">
                      <div class="form-group">
                        <label class="font-weight-bold text-uppercase">Nama Lengkap</label>
                        <input type="text" v-model="comment.name" class="form-control" placeholder="Masukkan Nama Lengkap">
                        <div v-if="validation.name" class="mt-2">
                          <b-alert show variant="danger">{{ validation.name[0] }}</b-alert>
                        </div>
                      </div>
                    </b-col>
                    <b-col md="6" sm="6">
                      <div class="form-group">
                        <label class="font-weight-bold text-uppercase">Alamat Email</label>
                        <input type="email" v-model="comment.email" class="form-control" placeholder="Masukkan Alamat Email">
                        <div v-if="validation.email" class="mt-2">
                          <b-alert show variant="danger">{{ validation.name[0] }}</b-alert>
                        </div>
                      </div>
                    </b-col>
                    <b-col md="12">
                      <div class="form-group">
                        <label class="font-weight-bold text-uppercase">Komentar</label>
                        <textarea class="form-control" v-model="comment.comment" rows="4" placeholder="Masukkan Komentar Positif"></textarea>
                        <div v-if="validation.comment" class="mt-2">
                          <b-alert show variant="danger">{{ validation.comment[0] }}</b-alert>
                        </div>
                      </div>
                    </b-col>
                    <b-col md="12">
                      <b-button size="sm" variant="info" type="submit">KIRIM</b-button>
                      <b-button size="sm" variant="light" type="reset">RESET</b-button>
                    </b-col>
                  </b-row>
                </b-form>
              </b-card-body>
            </b-collapse>
          </b-card>
        </b-col>
  
        <b-col md="4" sm="12">
          <b-card no-body class="border-0 rounded-lg shadow-md">
            <b-card-body>
              <h6 class="text-bold"><svg data-name="Layer 2" aria-hidden="true" width="20" height="20" class="mr-1" id="e73e2821-510d-456e-b3bd-9363037e93e3" viewBox="0 0 35 35" xmlns="http://www.w3.org/2000/svg"><path d="M11.933,15.055H3.479A3.232,3.232,0,0,1,.25,11.827V3.478A3.232,3.232,0,0,1,3.479.25h8.454a3.232,3.232,0,0,1,3.228,3.228v8.349A3.232,3.232,0,0,1,11.933,15.055ZM3.479,2.75a.73.73,0,0,0-.729.728v8.349a.73.73,0,0,0,.729.728h8.454a.729.729,0,0,0,.728-.728V3.478a.729.729,0,0,0-.728-.728Z"/><path d="M11.974,34.75H3.52A3.233,3.233,0,0,1,.291,31.521V23.173A3.232,3.232,0,0,1,3.52,19.945h8.454A3.232,3.232,0,0,1,15.2,23.173v8.348A3.232,3.232,0,0,1,11.974,34.75ZM3.52,22.445a.73.73,0,0,0-.729.728v8.348a.73.73,0,0,0,.729.729h8.454a.73.73,0,0,0,.728-.729V23.173a.729.729,0,0,0-.728-.728Z"/><path d="M31.522,34.75H23.068a3.233,3.233,0,0,1-3.229-3.229V23.173a3.232,3.232,0,0,1,3.229-3.228h8.454a3.232,3.232,0,0,1,3.228,3.228v8.348A3.232,3.232,0,0,1,31.522,34.75Zm-8.454-12.3a.73.73,0,0,0-.729.728v8.348a.73.73,0,0,0,.729.729h8.454a.73.73,0,0,0,.728-.729V23.173a.729.729,0,0,0-.728-.728Z"/><path d="M27.3,15.055a7.4,7.4,0,1,1,7.455-7.4A7.437,7.437,0,0,1,27.3,15.055Zm0-12.3a4.9,4.9,0,1,0,4.955,4.9A4.935,4.935,0,0,0,27.3,2.75Z"/></svg> KATEGORI</h6>
              <hr>
              <b-card no-body class="border-0 shadow-sm mb-2 rounded-lg" v-for="category in categories" :key="category.id">
                <b-card-body class="p-2 fw-normal btn btn-light text-left">
                  <b-img :src="category.image" width="40" class="rounded mr-1"></b-img>
                  <nuxt-link :to="{name: 'category-slug', params: {slug: category.slug}}" class="text-dark">{{ category.name }}</nuxt-link>
                </b-card-body>
              </b-card>
            </b-card-body>
          </b-card>
  
          <b-card no-body class="border-0 rounded-lg shadow-sm">
            <b-card-body>
              <h6 class="text-bold"><svg enable-background="new 0 0 48 48" class="mr-1" aria-hidden="true" height="22" id="Layer_1" version="1.1" viewBox="0 0 48 48" width="22" xml:space="preserve" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"><path clip-rule="evenodd" d="M46.996,24.983v0.021c0,0.32-0.16,0.593-0.395,0.776L27.662,44.719  c-0.381,0.381-0.998,0.381-1.381,0c-0.381-0.382-0.381-1,0-1.381l18.715-18.715v-6.619c0-0.552,0.449-1,1-1c0.553,0,1,0.448,1,1  v6.973C46.996,24.979,46.996,24.98,46.996,24.983z M19.806,46.575c-0.032,0.048-0.053,0.102-0.095,0.144  c-0.197,0.196-0.457,0.287-0.715,0.281c-0.258,0.006-0.518-0.085-0.715-0.281c-0.042-0.042-0.062-0.096-0.095-0.144L1.425,29.813  c-0.048-0.032-0.101-0.053-0.144-0.095C1.084,29.521,0.995,29.262,1,29.004c-0.006-0.258,0.084-0.518,0.281-0.715  c0.043-0.042,0.096-0.062,0.144-0.095L24.221,5.398c0.183-0.234,0.455-0.395,0.775-0.395h0.021c0.002,0,0.004,0,0.006,0h4.029  c0.133-1.502,0.746-2.82,1.67-3.683l0.016,0.018c0.195-0.207,0.463-0.335,0.758-0.335c0.592,0,1.072,0.512,1.072,1.143  c0,0.375-0.18,0.691-0.441,0.899c-0.479,0.442-0.82,1.139-0.934,1.958h4.775c0.002,0,0.004,0,0.008,0h0.02  c0.32,0,0.594,0.16,0.775,0.395l5.83,5.83c0.234,0.183,0.395,0.456,0.395,0.776v0.021c0,0.002,0,0.004,0,0.006v10.945  c0,0.002,0,0.004,0,0.007v0.021c0,0.32-0.16,0.593-0.395,0.775L19.806,46.575z M40.996,12.385l-5.381-5.381h-4.213  c0.176,0.444,0.424,0.822,0.725,1.1l0,0c0.041,0.033,0.092,0.053,0.127,0.092l0.018-0.018c1.041,0.973,1.725,2.508,1.725,4.254  c0,0.042-0.01,0.079-0.012,0.12c1.197,0.691,2.012,1.97,2.012,3.452c0,2.209-1.791,4-4,4s-4-1.791-4-4  c0-2.147,1.695-3.885,3.82-3.982c-0.09-0.888-0.441-1.648-0.949-2.118c-0.041-0.033-0.092-0.053-0.129-0.092L30.723,9.83  c-0.744-0.695-1.293-1.685-1.553-2.826h-3.793l-22,22l15.619,15.619l22-22V12.385z M30.867,14.961  c0.248-0.229,0.451-0.537,0.617-0.883c-0.855,0.228-1.488,1-1.488,1.925c0,1.104,0.896,2,2,2c1.105,0,2-0.896,2-2  c0-0.473-0.17-0.901-0.445-1.244c-0.615,1.545-1.297,1.909-1.297,1.909c-0.193,0.207-0.461,0.334-0.758,0.334  c-0.592,0-1.07-0.512-1.07-1.143C30.426,15.486,30.605,15.17,30.867,14.961z M12.282,27.289c0.382-0.381,1-0.381,1.381,0  l7.049,7.049c0.381,0.381,0.381,0.999,0,1.381c-0.381,0.381-1,0.381-1.381,0l-7.049-7.049  C11.901,28.289,11.901,27.671,12.282,27.289z M16.282,23.289c0.382-0.381,1-0.381,1.381,0l7.049,7.049  c0.38,0.381,0.38,0.999,0,1.381c-0.381,0.381-1,0.381-1.381,0l-7.049-7.049C15.901,24.289,15.901,23.671,16.282,23.289z" fill-rule="evenodd"/></svg> TAG</h6>
              <hr>
              <nuxt-link :to="{name: 'tag-slug', params:{slug: tag.slug}}" class="tag-badge badge badge-light btn-sm mb-2 mr-2 shadow-sm" v-for="tag in tags" :key="tag.id" :style="{ backgroundColor: getRandomColor() }">{{ tag.name }}</nuxt-link>
            </b-card-body>
          </b-card>
  
        </b-col>
      </b-row>
    </b-container>
</template>
  
<script>

    import Share from '@/components/Share.vue';

    export default {

      components: {
        Share,
      },
  
      //meta
      head() {
        return {
          title: this.post.title,
          meta: [
            {
              hid: 'og:title',
              name: 'og:title',
              content: this.post.title
            },
            {
              hid: 'og:site_name',
              name: 'og:site_name',
              content: this.post.title
            },
            {
              hid: 'og:image',
              name: 'og:image',
              content: this.post.image
            },
            {
              hid: 'description',
              name: 'description',
              content: this.post.description
            },
          ]
        }
      },
  
      async asyncData({ params, $axios }) {

        // Share
  
        //fetching post
        const post = await $axios.$get(`/api/web/posts/${params.slug}`)
  
        //fetching categories
        const categories = await $axios.$get('/api/web/categorySidebar')
  
        //fetching tags
        const tags = await $axios.$get('/api/web/tags')
  
        return {
          'post': post.data,
          'categories': categories.data,
          'tags': tags.data
        }
      },
  
      /**
      * kirim komentar
      */
      data() {
          return {
            //state comment
            comment: {
              name: '',
              email: '',
              comment: ''
            },
              //state validation
            validation: [],
            tags: [],
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
        },
  
        //metthod storeComment
        async storeComment() {
  
          //sending data to server
          await this.$axios.post('/api/web/posts/storeComment', {
  
            //data
            name: this.comment.name,
            email: this.comment.email,
            comment: this.comment.comment,
            slug: this.$route.params.slug
          })
          .then(() => {
  
            //feresh data
            this.$nuxt.refresh()
  
            //clear form
            this.comment.name = ''
            this.comment.email = ''
            this.comment.comment = ''
  
            //show sweet alert
            this.$swal.fire({
              title: '😊: BERHASIL!',
              text: "Komentar Anda Berhasil Terkirim!",
              icon: 'success',
              showConfirmButton: false,
              timer: 3000
            })
  
            this.$router.push({ path: this.$route.path });
  
          })
          .catch(error => {
  
            //assign error validation
            this.validation = error.response.data
  
          })
        }
  
      }
  
    }
</script>
  
<style>

  .no-copy {
    user-select: none;
  }

  .ckeditor-content img {
    display: block;
    max-width: 100%;
    height: auto;
  }
  @media (max-width: 768px) {
    .ckeditor-content img {
      display: block;
      max-width: 100%;
      height: auto;
    }

    .profil-center {
      text-align: center;
    }
  }

  .tag-badge {
    display: inline-block;
    color: #fff;
  }

  .donasi-trakteer {
    width: 150px;
    height: 50px;
    padding: 10px;
    background: #edf2f7;
    border-radius: 0.5rem;
    border: 3px solid darkblue;
    margin-right: 10px;
    margin-left: 10px;
    color: darkblue;
  }

  .donasi-trakteer:hover {
    background: lightblue;
    color: darkblue;
  }

  .donasi-saweria {
    width: 150px;
    height: 50px;
    padding: 10px;
    background: #edf2f7;
    border-radius: 0.5rem;
    border: 3px solid green;
    margin-right: 10px;
    margin-left: 10px;
    color: green;
  }

  .donasi-saweria:hover {
    background: lightgreen;
    color: green;
  }

  .donasi-qris {
    width: 150px;
    height: 50px;
    padding: 10px;
    background: #edf2f7;
    border-radius: 0.5rem;
    border: 3px solid maroon;
    margin-right: 10px;
    margin-left: 10px;
    color: maroon;
  }

  .donasi-qris:hover {
    background: lightcoral;
    color: maroon;
  }
</style>