<template>
  <div id="app">
    <HeaderComponent class="headerComp"/>
    <router-view class="routerItem"/>
    <FooterComponent class="footerComp"/>
  </div>
</template>

<script>
import HeaderComponent from "./components/header-component.vue";
import FooterComponent from "./components/foot-comp.vue";
export default {
  components:{
    HeaderComponent,
    FooterComponent
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
}
.footerComp{
  position: absolute;
  bottom: 0;
  left: 0;
}
</style>
