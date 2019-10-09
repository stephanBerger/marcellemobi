
<template>
  <div class="container-show">
    <header>
      <button
        style="position: fixed; top:110px"
        type="button"
        class="btn btn-warning border-warning"
      >
        <a :href="movie.trajet" target="_blank">Y aller</a>
      </button>
    </header>
    <h1 class="d-flex flex-column align-items-center">
      {{movie.title}}
      <span style="font-size: 0.4em">({{movie[ "Date de sortie"]}})</span>
    </h1>
    <div class="movie-credits d-flex flex-column justify-content-start align-items-center">
      <p>
        Produit par
        <span>{{movie["Produit Par"]}}</span>
      </p>
      <p>
        Réalisateur
        <span>{{movie["Réalisé par"]}}</span>
      </p>
      <p>
        Principaux interprètes
        <span>{{movie["Principaux Interprétes"]}}</span>
      </p>
      <img style="width: 70%" v-bind:src="movie.Affiche" />
      <!-- <p>{{movie["Affiche"]}}</p> -->

      <p style="margin: 2em 5em; text-align: justify;">{{movie["Synopsis"]}}</p>
    </div>
  </div>
</template>

<script>
import movies from '~/static/movies_json.json'

export default {
  data() {
    return {
      movie: {}
    }
  },
  mounted() {
    // Aller chercher le movie avec cet id
    // console.log(parseInt(this.$route.params.id))

    const movie = movies.find(
      movie => movie.id === parseInt(this.$route.params.id)
    )
    this.movie = movie
  }
}
</script>

<style lang="scss">
.container-show {
  margin-top: 4em;
  color: white;
}
.container-show span {
  margin-bottom: 4em;
}
.movie-credits p {
  font-size: 0.8em;
  margin-bottom: 2em;
}
.movie-credits span {
  background-color: #165da4;
  padding: 0.7em;
  border-radius: 4px;
  // width: 35vw;
  font-size: 0.8em;
  margin-bottom: 1em;
}
.container-show h1 {
  font-weight: 300;
}
.movie-credits {
  // width: 60vw;
}
</style>
