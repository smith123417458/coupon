<template>
  <div>
    
    

    <Intro />

    

 

   
  
  </div>

</template>

<script>
export default {
  methods: {
    goPage(selectedCategory) {
      this.$store.dispatch('changeCategory', selectedCategory);
      this.$router.push('/product');
    },
  },

  components: {

    

      Intro: () => import('@/components/Intro'),
  
    

     



   
   
  },
};
</script>
