<template>
  <div id="app"><MenuVue ref="iconInput"></MenuVue> <HomeVue></HomeVue></div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import MenuVue from "./components/Menu";
import HomeVue from "./components/Home";

export default {
  name: "App",
  components: {
    HelloWorld,
    MenuVue,
    HomeVue
  }
};

window.addEventListener("resize", function() {
  if (window.innerWidth > 600) {
    var x = document.getElementById("myTopnav");
    x.className = "item-navlink-grp";
    document.getElementById("app").style.marginLeft = "0";
    document.body.style.backgroundColor = "white";
    document.body.style.opacity = "1.0";
    this.$refs.iconInput.activeClass = "fa fa-bars menu-txt";
  }
});
</script>

<style>
#app {
  margin: 0px;
  padding: 0px;
  transition: margin-left 0.5s;
}
</style>
