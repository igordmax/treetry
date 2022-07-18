<template>
<ul class="cd-accordion-menu">
  <TreeComponent/>
</ul>
</template>

<script>
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
</script>

<style>

</style>
