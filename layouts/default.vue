<template>
    <div>
      <!-- navbar -->
      <Navbar />
  
      <!-- content -->
      <Nuxt />
  
      <!-- footer -->
      <Footer />
  
    </div>
</template>
<script>
    import Navbar from '@/components/web/navbar.vue'
    import Footer from '@/components/web/footer.vue'
    export default {
      components: {
        Navbar,
        Footer
      },
    }
</script>
  
<style>
    body {
      background-color: #ccdcec !important;
    }

    .jumbotron {
      background: #20303C !important;
      color: white;
    }
  
    .bg-navbar {
      background: #4C6A85;
    }
  
    .btn-primary {
      background-color: white;
      border-color: white;
      color: black;
    }
  
    .btn-primary:hover {
      background-color: #20303C;
      border-color: #20303C;
    }
  
    .btn-primary-dark {
      background-color: #0f456b;
      border-color: #20303C;
      color: white;
    }
  
    .btn-primary-dark:hover {
      color: white;
    }
  
    .carousel-item .img-fluid {
      border-radius: .5rem;
    }
  
    .card-category {
      background-color: #dadada;
    }
  
    .object-fit-cover {
      object-fit: cover;
    }
  
    .footer-top {
      background-color: #4C6A85;
      color: white;
    }
  
    .footer-bottom {
      background-color: #20303C;
    }
</style>