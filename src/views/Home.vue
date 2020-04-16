<template>
  <div>
    <header>
      <Navbar />
    </header>

   
    <main>
      <router-view  />
    </main>
    
    

 
   
  </div>
</template>


<script>
export default {
  components: {
 
    Navbar: () => import('@/components/Navbar'),
 
  





}}
</script>
