<template>
    <div class="container-series">
      <div class="d-flex justify-content-between overflow-auto scrollbar">
        <CardSeries
          v-for="(elem, index) in arraySeriesApp"
          :key="index"
          :ObjectSeries="elem"
        />
      </div>
    </div>
  </template>
  
  <script>
  import CardSeries from "./CardSeries.vue";
  
  export default {
    name: "SeriesList",
  
    components: {
      CardSeries,
    },
  
    props: {
  
      arraySeriesApp: Array,
  
    },
  
  };
  </script>
  
  <style lang="scss" scoped>
  
  .container-series{
    
    width: 80%;
    margin: 0 auto;
  }
  
  .scrollbar::-webkit-scrollbar{
      background-color: rgba(27, 27, 27, 1);
      height: 10px;
  }
  
  .scrollbar::-webkit-scrollbar-thumb {
    background-color: black;
    border-radius: 20px;
  }
  </style>