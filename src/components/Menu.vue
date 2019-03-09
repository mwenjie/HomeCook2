<template>
  <div>
    <link
      rel="stylesheet"
      href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css"
    />
    <div class="navmenu">
      <div class="item-logo-grp">
        <div id="logo"></div>
        <div class="menu-txt" id="logo-txt">Home<br />Cook</div>
      </div>
      <div class="item-navlink-grp" id="myTopnav">
        <a href="/cook" class="menu-txt">Cook</a>
        <a href="/buy" class="menu-txt">Dine</a>
        <a href="/login" class="menu-txt">Login</a>
        <a href="/signup" class="menu-txt">Sign Up</a>
        <a href="javascript:void(0);" class="icon" v-on:click="openNav">
          <i v-bind:class="[activeClass]"></i>
        </a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: "Hello Vue.js!",
      activeClass: "fa fa-bars menu-txt"
    };
  },
  // define methods under the `methods` object
  methods: {
    openNav: function(event) {
      var x = document.getElementById("myTopnav");
      if (x.className === "item-navlink-grp") {
        x.className += " responsive";
        document.getElementById("app").style.marginLeft = "240px";
        document.body.style.backgroundColor = "rgba(0,0,0,.6)";
        document.body.style.opacity = "0.65";
        this.activeClass = "fa fa-times menu-txt";
      } else {
        x.className = "item-navlink-grp";
        document.getElementById("app").style.marginLeft = "0";
        document.body.style.backgroundColor = "white";
        document.body.style.opacity = "1";
        this.activeClass = "fa fa-bars menu-txt";
      }
    }
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Luckiest+Guy");
@import url("https://fonts.googleapis.com/css?family=Lato");

.navmenu {
  display: flex;
  flex-direction: row;
  border-bottom: 25px solid #ffaa2a;
  white-space: nowrap;
  margin-top: 5px;
}

.menu-txt {
  font-family: "Luckiest Guy";
  font-style: normal;
  font-weight: normal;
  color: #ffaa2a;
}

.item-logo-grp {
  flex-grow: 6;
  display: inline;
  white-space: nowrap;
  margin-left: 5px;
}

#logo {
  width: 37px;
  height: 34px;
  background: url("https://i.ibb.co/jMgr9Bj/logo.png");
  background-repeat: no-repeat;
  float: left;
  margin-top: 2px;
  margin-right: 2px;
}

#logo-txt {
  line-height: 22px;
  font-size: 24px;
}

.item-navlink-grp {
  flex-grow: 0;
  margin-top: 10px;
}

.item-navlink-grp a {
  text-decoration: none;
  font-size: 20px;
  padding: 20px;
}

.item-navlink-grp .icon {
  display: none;
}

@media screen and (max-width: 600px) {
  .item-navlink-grp a:not(:last-child) {
    display: none;
  }
  .item-navlink-grp a:last-child {
    display: inline;
  }
}

@media screen and (max-width: 600px) {
  .item-navlink-grp.responsive {
    height: 100%;
    width: 250px;
    position: fixed;
    z-index: 1;
    top: 0;
    left: 0;
    background-color: black;
    margin: 0px;
  }
  .item-navlink-grp.responsive a.icon {
    position: absolute;
    right: 0;
    top: 0;
  }
  .item-navlink-grp.responsive a {
    float: none;
    display: block;
    text-align: left;
  }
}
</style>
