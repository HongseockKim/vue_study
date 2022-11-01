<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="props"/>
    <CommonList :isSet="isList()"/>
    <TestComponent bigtext="요렇게 Props 담아서 넘기면"/>
    <div>
      <button @click="isToClick()" type="button">{{ name }}</button>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TestComponent from "./components/TestComponent";
import CommonList from "./components/CommonList";

export default {
  data(){
    return{
      name: '닫힘',
      isOpen: false,
      isListSet : false,
    }
  },
  components: {
    HelloWorld,
    TestComponent,
    CommonList
  },
  methods:{
    isToClick: function (  ){
      if(this.isOpen){
        this.isOpen = false;
        this.name = "닫힘";
      } else {
        this.isOpen = true;
        this.name = "열림";
      }
      this.isList();
      return this.isOpen
    },
    isList: function (  ){
      var isClick = this.isOpen;
      isClick ? this.isListSet = true : this.isListSet = false
      return this.isListSet;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
