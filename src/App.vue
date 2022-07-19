<template>
 <div class="container center">
  
  <ul class="cd-accordion-menu">
    
<TreeComponent :model="TreeComponent"></TreeComponent>
</ul>
</div>
</template>

<script>

import TreeComponent from './components/TreeComponent.vue'
export default {
  name: 'App',
  components: {
    TreeComponent 
  },

};
</script>

<style>

</style>