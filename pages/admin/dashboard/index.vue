<template>
    <!-- Content Wrapper. Contains page content -->
    <div class="content-wrapper">
      <section class="content-header">
        <div class="container-fluid">
        </div>
      </section>
  
      <section class="content">
        <div class="row">
          <div class="col-md-4 col-sm-6 col-12">
            <div class="info-box">
              <span class="info-box-icon bg-primary"><i class="fa fa-upload"></i></span>
              <div class="info-box-content">
                <span class="info-box-text">JUMLAH POST ARTIKEL</span>
                <span>
                  <hr></span>
                <span class="h3 info-box-number">{{ posts }}</span>
              </div>
            </div>
          </div>
          <div class="col-md-4 col-sm-6 col-12">
            <div class="info-box">
              <span class="info-box-icon bg-info"><i class="fa fa-tags"></i></span>
              <div class="info-box-content">
                <span class="info-box-text">JUMLAH TAG</span>
                <span>
                  <hr>
                </span>
                <span class="h3 info-box-number">{{ tags }}</span> 
              </div>
            </div>
          </div>
          <div class="col-md-4 col-sm-6 col-12">
            <div class="info-box">
              <span class="info-box-icon bg-maroon"><i class="fa fa-list"></i></span>
              <div class="info-box-content">
                <span class="info-box-text">JUMLAH KATEGORI</span>
                <span>
                  <hr></span>
                <span class="h3 info-box-number">{{ categories }}</span>
              </div>
            </div>
          </div>
          <div class="col-md-3 col-sm-6 col-12">
            <div class="info-box">
              <span class="info-box-icon bg-success"><i class="fa fa-comments"></i></span>
              <div class="info-box-content">
                <span class="info-box-text">JUMLAH KOMENTAR</span>
                <span>
                  <hr></span>
                <span class="h3 info-box-number">{{ comments }}</span>
              </div>
            </div>
          </div>
          <div class="col-md-3 col-sm-6 col-12">
            <div class="info-box">
              <span class="info-box-icon bg-secondary"><i class="fa fa-bars"></i></span>
              <div class="info-box-content">
                <span class="info-box-text">JUMLAH MENU</span>
                <span>
                  <hr></span>
                <span class="h3 info-box-number">{{ menus }}</span>
              </div>
            </div>
          </div>
          <div class="col-md-3 col-sm-6 col-12">
            <div class="info-box">
              <span class="info-box-icon bg-danger"><i class="fa fa-images"></i></span>
              <div class="info-box-content">
                <span class="info-box-text">JUMLAH SLIDERS</span>
                <span>
                  <hr></span>
                <span class="h3 info-box-number">{{ sliders }}</span>
              </div>
            </div>
          </div>
          <div class="col-md-3 col-sm-6 col-12">
            <div class="info-box">
              <span class="info-box-icon bg-dark"><i class="fa fa-users"></i></span>
              <div class="info-box-content">
                <span class="info-box-text">JUMLAH PENGGUNA</span>
                <span>
                  <hr></span>
                <span class="h3 info-box-number">{{ users }}</span>
              </div>
            </div>
          </div>
        </div>
  
      </section>
    </div>
</template>
  
<script>
    export default {
      //layout
      layout: 'admin',
  
      //meta
      head() {
        return {
          title: 'Dashboard - portal.helmisalsabila.com',
        }
      },
  
      async asyncData({ $axios }) {
  
        //fetching dashboard
        const dashboard = await $axios.$get('/api/admin/dashboard')
  
        return {
          'users': dashboard.data.users,
          'tags' : dashboard.data.tags,
          'posts': dashboard.data.posts,
          'categories': dashboard.data.categories,
          'menus' : dashboard.data.menus,
          'sliders': dashboard.data.sliders,
          'comments': dashboard.data.comments,
        }
      },
  
    }
</script>
  
<style>
  
</style>