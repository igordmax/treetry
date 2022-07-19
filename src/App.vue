<template>
 <div class="container center" id="demo">
  
  <ul class="cd-accordion-menu">
    
    <TreeComponent :model="treeData"></TreeComponent>
    
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