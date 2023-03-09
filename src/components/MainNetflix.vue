<template>
  <div class="container-main">
    <div>
      <h3>FILM</h3>
      <FilmList :arrayResultApp="arrayResultApp"/>
    </div>
    <div>
      <h3>SERIE TV</h3>
      <SeriesList :arraySeriesApp="arraySeriesApp"/>
    </div>

  </div>
</template>

<script>
import FilmList from './FilmList.vue'
import SeriesList from './SeriesList.vue'

export default {

    name: 'MainNetflix',

    components:{

      FilmList,
      SeriesList,

    },

    props:{

      arrayResultApp: Array,
      arraySeriesApp: Array

    }
};
</script>

<style lang="scss" scoped>

.container-main{

  width: 80%;
  margin: 0 auto;
}

div{

  background-color: rgba(27, 27, 27, 1);
  padding: 10px 0;
}

h3{
  color: white;

}
</style>