<template>
  <div>
    <navbar :logo="logo_src" :alt="alt_src"/>
    <router-view/>
    <Footer/>
  </div>
</template>

<script>

import Navbar from "@/components/Navbar";
import Footer from "@/components/Footer";

export default {
  name: 'App',
  components: {
    // eslint-disable-next-line vue/no-unused-components
    Navbar,
    Footer
  },
  data(){
    return {
      logo_src: "/img/logo.png",
      alt_src: "Make your banner"
    }
  }
}
</script>

<style>
  * {
    font-family: Roboto, Arial;
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  .main-container {
    margin: 50px;
    min-height: 250px;
  }
  h1 {
    text-align: center;
    font-size: 42px;
    margin-bottom: 30px;
    color: #222222;
    font-weight: 700;
  }
</style>
