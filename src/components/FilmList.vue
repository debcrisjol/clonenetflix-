<template>

  <div class="container-film">
    <div class="d-flex justify-content-between overflow-auto scrollbar">
      <CardNetflix
        v-for="(elem, index) in arrayResultApp"
        :key="index"
        :ObjectMovies="elem"
      />
    </div>
  </div>
</template>

<script>
import CardNetflix from "./CardNetflix.vue";

export default {
  name: "FilmList",

  components: {
    CardNetflix,
  },

  props: {
    arrayResultApp: Array,
  },
};
</script> 

<style lang="scss" scoped>

.scrollbar::-webkit-scrollbar {
  background-color: rgba(27, 27, 27, 1);
  height: 10px;
}
.scrollbar::-webkit-scrollbar-thumb {
  background-color: black;
  border-radius: 20px;
}
.container-film{

  width: 80%;
  margin: 0 auto;
}
</style>