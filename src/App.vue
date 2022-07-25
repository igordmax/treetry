<template>
 <div class="container center">
  
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
    data: function() {
    return {
      treeData: treeData
    }
  }, 

};
let treeData= {

        name: "group",        
  children: [
    {
      name: "Sub Group",
      children: [{ name: "Item" }, { name: "Item" }]
    },
     {
      name: "Sub Group1",
      children: [
        { name: "Item1" }, 
        { name: "Item1", 
         children: [
           {name: "subsub"}
         ]
        }
      ]
     },
    { name: "Item" }
  ] 
                };
</script>

<style>

</style>