<template>
  <div id="topbox">
    <img src="../assets/logo.png" height="120">
    <span id="appName">Random<br>Draw</span>
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
  #topbox {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 20px;
    animation-name: logo_image; 
    animation-duration: 3s;
    position: relative;
    border-bottom: 2px solid brown;
    
  }

  #appName {
    font-family: 'Zen Tokyo Zoo', cursive;
    font-size: 48px;
    color: white;
    margin-left: 10px;
  }

  @keyframes logo_image {
    0% {
      top: 1000px;
    }

    100% {
      top: 0px;
    }
  }

  

  
  

  /* On screens that are 992px or less, set the background color to blue */
  @media screen and (max-width: 992px) {
    
  }

  /* On screens that are 600px or less, set the background color to olive */
  @media screen and (max-width: 600px) {
    
  }
</style>