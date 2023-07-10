<template>
    <div class="content-wrapper">
      <section class="content-header">
        <div class="container-fluid">
        </div>
      </section>
  
      <section class="content">
        <div class="card card-outline card-info">
          <div class="card-header">
            <h3 class="card-title"><i class="nav-icon fa fa-images mr-1"></i> EDIT SLIDER</h3>
            <div class="card-tools">
              <button type="button" class="btn btn-tool" data-card-widget="collapse" title="Collapse">
                <i class="fas fa-minus"></i>
              </button>
              <button type="button" class="btn btn-tool" data-card-widget="remove" title="Remove">
                <i class="fas fa-times"></i>
              </button>
            </div>
          </div>
          <div class="card-body">
            <form @submit.prevent="updateSlider">
  
              <div class="form-group">
                <label>GAMBAR SLIDER</label>
                <input type="file" @change="handleFileChange" class="form-control btn-sm">
              </div>
  
              <button class="btn btn-info mr-1 btn-submit" type="submit"><i class="fa fa-paper-plane mr-1"></i> UPDATE</button>
              <button class="btn btn-warning btn-reset" type="reset"><i class="fa fa-redo mr-1"></i> RESET</button>
  
            </form>
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
          title: 'Edit Slider - portal.helmisalsabila.com',
        }
      },
  
      data() {
        return {
          //state slider
          slider: {
            image: '',
          },
          //state validation
          validation: []
        }
      },
      
      mounted() {
        this.$axios.get(`/api/admin/sliders/${this.$route.params.id}`)
          .then(response => {  
            this.slider.image = response.data.data.image
          })
      },
  
      methods: {
  
        handleFileChange(e) {
  
          //get image
          let image = this.slider.image = e.target.files[0]
  
          //check fileType
          if (!image.type.match('image.*')) {
  
            //if fileType not allowed, then clear value and set null
            e.target.value = ''
  
            this.slider.image = null
  
            //show sweet alert
            this.$swal.fire({
              title: '😣: OOPS!',
              text: "Format File Tidak Didukung!",
              icon: 'error',
              showConfirmButton: false,
              timer: 2000
            })
          }
  
        },
  
        //storeSlider method
        async updateSlider() {
  
          //define formData
          let formData = new FormData();
  
          formData.append('image', this.slider.image)
          formData.append("_method", "PATCH")
  
          //sending data to server
          await this.$axios.post(`/api/admin/sliders/${this.$route.params.id}`, formData)
            .then(() => {
  
              //sweet alert
              this.$swal.fire({
                title: '😊: BERHASIL!',
                text: "Data Berhasil Disimpan!",
                icon: 'success',
                showConfirmButton: false,
                timer: 2000
              })
  
              //redirect, if success store data
              this.$router.push({
                name: 'admin-slider'
              })
  
            })
            .catch(error => {
  
              //assign error to state "validation"
              this.validation = error.response.data
            })
        }
      }
  
    }
</script>
  
<style>
  
</style>