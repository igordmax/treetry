<template>
<li :class="[isFolder ? 'folder' : 'file']">
 
   <label id=clickToAct @click="makeActive" 
   >
          <button>
      <span :class="{'open': open}"
      @click="toggle">
      </span>
     </button> 
          
      {{ model.name }} 

    </label>
    <ul v-show="open" v-if="isFolder" :class="{'open': open}">
      <TreeComponent
        v-for="(model, index) in model.children"
        :key="index"
        :model="model">
      </TreeComponent>
    </ul>
  </li>
</template>

<script>

export default {
  name: 'TreeComponent',
  props: {
    model: Object
  },
 
  computed: {
    isFolder: function(){
     return this.model.children && this.model.children.length;
    }
  },
  methods: {
    stopClick: function (e) {
      e.preventDefault();
    },
    toggle: function () {
      if (this.isFolder) {
        this.open= !this.open;
      }
    }
  },
 

};

</script>

<style>

</style>
