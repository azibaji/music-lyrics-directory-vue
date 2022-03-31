<template>
    <div class="container pt-4 text-center">
        <search-box @lyricFinder="lyricFinder" />
        <div v-for="music in musics" :key="music.id">
            <music-item :music="music"/>
        </div>
        
    </div>
</template>
<script>
import SearchBox from '../components/shared/SearchBox.vue'
import axios from 'axios'
import musicItem from '../components/music/musicItem.vue'
export default {
    data: () =>({
        musics:[]
    }),
    components:{
        SearchBox,
        musicItem
    },
    methods:{
        lyricFinder(song){
          axios.get(`https://api.lyrics.ovh/suggest/${song}`).then(
              (response) =>{
                  if(response.data){
                      this.musics = response.data.data
                      console.log(this.musics)
                  }
              }
          ).catch(function(error){
            console.log(error)
        })
        }
    }
}
</script>
<style scoped>

</style>