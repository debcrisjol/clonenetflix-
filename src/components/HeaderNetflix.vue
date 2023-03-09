<template>
    <header>
      <div class="container-header d-flex align-items-center justify-content-around">
  
        <div>
          <img src="../assets/Netflix-Logo.wine.png" alt="#">
        </div>
         <div class="w-75">
       
          <input class="m-2 bg-seccondary text-black" type="text" placeholder="Search Movie" aria-label="default input example" v-model="searchText" @keyup="$emit('emitSearchTextHeader', searchText)">
        </div>
      </div>
      
    </header>
  </template>
  
  <script>
  export default {
    name: 'HeaderNetflix',
    props: {
      
    },
    data(){
      return {
  
        searchText: '',
  
      }
    },
  }
  </script>
  
  <!-- Add "scoped" attribute to limit CSS to this component only -->
  <style scoped lang="scss">
  
  header{
  
    background-color: black;
  }
  
  img{
    width: 20%;
  }
  @media (max-width: 28.75em){
    img{width:50%;}
  }
  .container-header{
  
    width: 80%;
    margin: 0 auto;
  }
  
  </style>
