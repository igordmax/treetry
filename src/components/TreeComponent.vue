<template>
  <TreeComponent :model="treeData"></TreeComponent>
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
  template: `
  <li :class="[isFolder ? 'folder' : 'file']">
    <label id=clickToAct @click="makeActive">
      <button>
        <span :class="{'open': open}"
        @click="toggle">
        </span>
      </button> 
        {{ model.name }}
    </label>

    <ul v-show="open" v-if="isFolder" :class="{'open': 'open'}">
      <TreeComponent
        v-for="(model, index) in model.children"
        :key="index"
        :model="model">
      <TreeComponent>    
    </ul>
  </li>`
};

</script>

<style>
*, *::after, *::before {
  box-sizing: padding-box;
}

body {
  color: rgba(255,255,255,1);
  background: rgba(255,255,255,1);
 
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", Helvetica, Arial,
    sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  overflow: hidden;
}

html,
body,
.container {
  min-height: 100vh;
}


.left {
  display: flex;
  justify-content: left;
  align-items: left;
}

ol, ul {
	list-style: none;
  padding: 0px;
}


.cd-accordion-menu {
  width: 90%;
  max-width: 600px;
  margin: 0;
    background: rgba(237,245,250,1)
 
}

.cd-accordion-menu li {
  user-select: none;
  
}


.cd-accordion-menu label, .cd-accordion-menu a {
  position: relative;
  display: block;
  padding: 18px 18px 18px 45px;
  box-shadow: inset 1px 1px #000;
  
  color: rgba(0,0,0,.8);
}

.cd-accordion-menu label::before,
.cd-accordion-menu label::after,
.cd-accordion-menu a::after {
  /* icons */
  content: '';
  display: inline-block;
  width: 16px;
  height: 16px;
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
}
.cd-accordion-menu label {
  cursor: pointer;
}

.cd-accordion-menu button {     
    background-color: Transparent;
    background-repeat:no-repeat;
    border: none;
    cursor:pointer;
    overflow: hidden;        
}

/*adding icons*/
.cd-accordion-menu li.folder >label> button span::before {
  content: "\f054";
}
.cd-accordion-menu li.folder >label> button span.open::before {
   content: "\f078"
}
.cd-accordion-menu button>span:before {
  /* arrow icon */
    font: normal 14px/1 FontAwesome;
  left: 18px;
  /*transform: translateY(-50%);
  transition: transform 0.3s;*/
}
.cd-accordion-menu button span.open:before {
    /*transform: translateY(-25%) rotate(90deg);
*/
  left: 18px; 
}

.cd-accordion-menu ul label,
.cd-accordion-menu ul a {
  background: rgba(237,245,250,1);
  box-shadow: inset 0 -1px rgba(0,0,0,.29804);
  padding-left: 82px;
}
.cd-accordion-menu ul label:hover{
  background: rgba(218,235,247,1);
}
.cd-accordion-menu ul a:hover {
  background: rgba(218,235,247,1);
}
.cd-accordion-menu ul label:active{  

  box-shadow: inset 0 0 0 1.5px rgba(13,153,255,1);
}

.cd-accordion-menu ul a:active {
  background: #ffcd29;
}

.active{  

  box-shadow: inset 0 0 0 1.5px rgba(13,153,255,1);
}

.cd-accordion-menu > li:last-of-type > label,
.cd-accordion-menu > li:last-of-type > a,
.cd-accordion-menu > li > ul > li:last-of-type label,
.cd-accordion-menu > li > ul > li:last-of-type a {
  box-shadow: none;
}
.cd-accordion-menu ul label::before {
  left: 36px;
}
.cd-accordion-menu ul label::after,
.cd-accordion-menu ul a::after {
  left: 59px;
}
.cd-accordion-menu ul ul label,
.cd-accordion-menu ul ul a {
  padding-left: 100px;
}
.cd-accordion-menu ul ul label::before {
  left: 54px;
}
.cd-accordion-menu ul ul label::after,
.cd-accordion-menu ul ul a::after {
  left: 77px;
}
.cd-accordion-menu ul ul ul label,
.cd-accordion-menu ul ul ul a {
  padding-left: 118px;
}
.cd-accordion-menu ul ul ul label::before {
  left: 72px;
}
.cd-accordion-menu ul ul ul label::after,
.cd-accordion-menu ul ul ul a::after {
  left: 95px;
}
</style>
