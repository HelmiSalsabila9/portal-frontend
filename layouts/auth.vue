<template>
  <div class="hold-transition login-page">
    <div class="login-box">
      <!-- /.login-logo -->
      <Nuxt />
      <!-- /.card -->
    </div>
  </div>
</template>

<script>
  export default {

    //middleware auth
    middleware: 'auth',

  }
</script>

<style>
  body {
    font-family: 'Quicksand', sans-serif;
  }

  .login-page {
    background-color: #ccdcec !important;
  }

  .card-info.card-outline {
    border-top: 3px solid #4C6A85;
  }

  .btn-info {
    color: #fff;
    background-color: #4C6A85;
    border-color: #4C6A85;
    box-shadow: none
  }

  .btn-info:hover {
    color: #fff;
    background-color: #12466B;
    border-color: #12466B;
    box-shadow: none;
  }
</style>