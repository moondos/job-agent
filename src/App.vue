<template>
  <div id="app">
    
    <JobAgent/>
    
  </div>

</template>


<script>
    import JobAgent from "./components/JobAgent.vue"

    export default {
      components: {
        JobAgent,
      },
      
    }
</script> 

<style lang="scss">

@font-face {
  font-family: 'Roboto';
  src: local("Roboto"),
   url(./fonts/Roboto/Roboto-Regular.ttf) format("truetype");
}

#app {
  font-family: "Roboto";
  font-style: normal;
  font-weight: normal;
  font-size: 12px;
  line-height: 14px; 
  color: #636363;
}

</style>
