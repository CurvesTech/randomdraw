<template>
  <TopBar></TopBar>
  <ContentBox></ContentBox>
  <Footer></Footer>
</template>

<script>

import TopBar from './components/TopBar';
import ContentBox from './components/ContentBox';
import Footer from './components/Footer';
export default {
  name: 'App',
  components: {
    TopBar,
    ContentBox,
    Footer
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Lexend:wght@300&family=Zen+Tokyo+Zoo&display=swap');

  * {
    margin: 0;
    padding: 0;
  }

  body {
    background: rgb(56, 0, 56);
    color: white;
    font-family: 'Lexend', sans-serif;
  }

  
</style>
