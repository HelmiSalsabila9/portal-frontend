<template>
    <!-- Sidebar Menu -->
    <nav class="mt-2">
      <ul class="nav nav-pills nav-sidebar flex-column" data-widget="treeview" role="menu" data-accordion="false">
  
        <li class="nav-header">
          <h6>DASHBOARD</h6>
        </li>

        <li class="nav-item">
          <nuxt-link :to="{name: 'admin-dashboard'}" class="nav-link">
            <i class="nav-icon fas fa-tachometer-alt"></i>
            <p>
              Dashboard
            </p>
          </nuxt-link>
        </li>
  
        <li class="nav-header">
          <h6>KONTEN</h6>
        </li>
  
        <li class="nav-item">
          <nuxt-link :to="{name: 'admin-tag'}" class="nav-link">
            <i class="nav-icon fas fa-tags"></i>
            <p>
              Tag
            </p>
          </nuxt-link>
        </li>
  
        <li class="nav-item">
          <nuxt-link :to="{name: 'admin-category'}" class="nav-link">
            <i class="nav-icon fas fa-list mr-1"></i>
            <p>
              Kategori
            </p>
          </nuxt-link>
        </li>
  
        <li class="nav-item">
          <nuxt-link :to="{name: 'admin-post'}" class="nav-link">
            <i class="nav-icon fa fa-upload mr-1"></i>
            <p>
              Post Artikel
            </p>
          </nuxt-link>
        </li>
  
        <li class="nav-header">
          <h6>KONFIGURASI</h6>
        </li>
  
        <li class="nav-item">
          <nuxt-link :to="{name: 'admin-menu'}" class="nav-link">
            <i class="nav-icon fa fa-bars"></i>
            <p>
              Menu
            </p>
          </nuxt-link>
        </li>
  
        <li class="nav-item">
          <nuxt-link :to="{name: 'admin-slider'}" class="nav-link">
            <i class="nav-icon fas fa-image"></i>
            <p>
              Slider
            </p>
          </nuxt-link>
        </li>
  
        <li class="nav-item">
          <nuxt-link :to="{name: 'admin-user'}" class="nav-link">
            <i class="nav-icon fas fa-users"></i>
            <p>
              Pengguna
            </p>
          </nuxt-link>
        </li>

        <li class="nav-header">
          <h6>AKHIRI SESI</h6>
        </li>

        <li class="nav-item" style="cursor: pointer;">
          <a @click="logout" class="nav-link">
            <i class="nav-icon fas fa-sign-out-alt"></i>
            <p>
              Keluar
            </p>
          </a>
        </li> 

      </ul>
    </nav>
    <!-- /.sidebar-menu -->
</template>
  
<script>
    export default {

      methods: {

      async logout() {

        //logout auth
        await this.$auth.logout()

        //redirect route login
        this.$router.push({
          name: 'login'
        })

      }

    }
  
    }
</script>
  
<style scoped>
    a.nuxt-link-active {
      background-color: #4C6A85;
    }
</style>