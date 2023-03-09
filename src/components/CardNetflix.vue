<template>
  <div class="container-cards">
    {{ starsRating() }}
    <div class="card-img">
      <img
        v-if="ObjectMovies.poster_path"
        :src="`http://image.tmdb.org/t/p/w185/${ObjectMovies.poster_path}`"
        alt=""
      />
      <img
        class="img-null"
        v-else
        src="https://th.bing.com/th/id/OIP.AC9frNlqFnn-I2JCycN8fwHaEK?pid=ImgDet&rs=1"
        alt=""
      />
    </div>

    <div class="card-content p-3">
      <div>
        <span> <strong>Title: </strong> </span>{{ ObjectMovies.title }}
      </div>
      <div>
        <span> <strong>Original Title: </strong> </span
        >{{ ObjectMovies.original_title }}
      </div>
      <div>
        <span><strong>Language: </strong></span>

        <img
          :src="`https://www.countryflagicons.com/SHINY/64/${
            ObjectMovies.original_language == 'en'
              ? 'GB'
              : ObjectMovies.original_language == 'ja'
              ? 'JP'
              : ObjectMovies.original_language.toUpperCase()
          }.png`"
        />
      </div>

      <div>
        <span> <strong>Vote: </strong></span>{{ ObjectMovies.vote_average }}
      </div>

      <div>
        <div class="d-inline" v-for="n in fullStars" :key="'cardFullStars' + n">
          <font-awesome-icon icon="fa-solid fa-star" />
        </div>

        <div class="d-inline" v-if="halfStar == true">
          <font-awesome-icon icon="fa-regular fa-star-half-stroke" />
        </div>

        <div
          class="d-inline"
          v-for="n in emptyStars"
          :key="'cardEmptyStars' + n"
        >
          <font-awesome-icon icon="fa-regular fa-star" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CardNetflix",

  data() {
    return {
      halfVote: 0,
      fullStars: 0,
      emptyStars: 0,
      halfStar: false,
    };
  },

  props: {
    ObjectMovies: Object,
  },

  methods: {
    starsRating() {
      //divido per 2 il voto medio
      this.halfVote = this.ObjectMovies.vote_average / 2;
      // controllo se il voto a metà è un numero intero o no
      // se non è intero devo considerare che c'è una stella mezza piena quindi la variabile andrà su true per indicarne la presenza
      // le stelle piene saranno contate sulla base del voto a metà per difetto (perchè dopo c'è la mezza)
      // le stelle vuote sono 5 - le piene - una stella a metà
      if (this.halfVote != Math.floor(this.halfVote)) {
        this.halfStar = true;
        this.fullStars = Math.floor(this.halfVote);
        this.emptyStars = 4 - this.fullStars;
      }
      // in questo caso non c'è nessuna mezza stella
      else {
        this.halfStar = false;
        this.fullStars = this.halfVote;
        this.emptyStars = 5 - this.fullStars;
      }
    },
  },
};
</script>



<style lang="scss" scoped>
.img-null {
  width: 185px;
}
.container-cards {
  width: 185px;
  margin-right: 20px;
  padding: 20px;
}

.card-content {
  color: white;
}
.container-cards:hover .card-img,
.card-content {
  display: none;
}
.container-cards:hover .card-content {
  width: 185px;
  display: block;
}
.fa-star,
.fa-star-half-stroke {
  color: yellow;
}
</style>