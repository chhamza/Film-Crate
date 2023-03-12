<template>
  <v-container>
    <v-carousel
      hide-delimiter-background
      show-arrows="hover"
    >
      <v-carousel-item
        v-for="(slide, i) in slides"
        :key="i"
      >
        <v-sheet
          color="transparent"
          height="100%"
          style="background:rgba(56,255,255,0.9);"
        >
          <v-img id="container" :src="slide.bg" style="width: 100%; height: 100%;" >
            <div id="box" class="d-flex fill-height justify-center align-center">
              <div class="movie_desc">
                <div class="ml-2">
                  <h3> {{ slide.title }} </h3>
                  <p> {{ slide.genres }} </p>
                  <p> {{ slide.releaseDate }} </p>
                  <a :href=slide.trailerLink target="_blank">{{ slide.trailerLink }}</a>
                </div>
              </div>
              <div class="movie_poster">
                <v-img :src="slide.poster" />
              </div>
            </div>  
          </v-img>
        </v-sheet>
      </v-carousel-item>
    </v-carousel>
  </v-container>
</template>

<script>
  export default {
    data () {
      return {
        slides: [],
      }
    },
    beforeCreate() {
      setTimeout( () => {
        fetch('http://localhost:8080/api/v1/movies')
        .then( (resp) => {
            if(resp.status === 200){
                return resp.json();
            }
        })
        .then((data) => {
           data.forEach((movie) => {
            this.slides.push({
               title: movie.title,
               bg: movie.backdrops[0],
               poster: movie.poster,
               genres: movie.genres[0],
               releaseDate: movie.releaseDate,
               trailerLink: movie.trailerLink
             });
          });
        })
        .catch( (error) => {
            console.log(error);
        })
      }, 100);
    }
  }
</script>

<style scoped>
#box {
    background:rgba(205,206,255,0.3);
}
.movie_desc {
  width: 45%;
  height: 50%;
  border:1px solid #000; display:inline-block;
  color: white;
  margin-right: -200px;
  font-size: 22px;
  background-color: rgb(128, 128, 128, 0.7);
}
.movie_poster {
  width: 45%;
  height: 50%;
  display:inline-block;
  color: white;
}
</style>