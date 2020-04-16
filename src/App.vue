<template>
  <div id="app">
    
    <loading :active.sync="isLoading" :is-full-page="true">
       <template slot="default">
         <img src="@/assets/img/r01.png" width="50px"> 
      </template>
      <template slot="after">
        <img src="@/assets/img/loading.gif">
      </template>
      
      </loading> 
    <router-view />
  </div>
</template>


<script>
export default {
  computed: {
   
    isLoading() {
      return this.$store.state.isLoading;
    },
  },
  
  created() {
   
    this.$bus.$on('sweet-alert', (params) => {
      this.$swal.fire({
        position: 'top-end',
        ...params,
        showConfirmButton: false,
        timer: 2000,
        allowOutsideClick: false,
      });
    });

   
    this.$bus.$on('sweet-alert-info', (params) => {
      this.$swal.fire({
        ...params,
        showCloseButton: false,
        confirmButtonText: '已複製',
        buttonsStyling: false,
        customClass: {
          confirmButton: 'btn btn-dark btn-lg',
        },
      });
    });

    // goTop
    this.$bus.$on('goTop', () => {
      $('html, body')
        .stop()
        .animate(
          {
            scrollTop: $('html,body').offset().top,
          },
          1000,
        );
    });
  },
};
</script>
