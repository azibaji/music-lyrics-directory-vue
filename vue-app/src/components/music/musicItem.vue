<template>
    <div class="col-11 music">
        <div class="col-2">
            <img :src="music.album.cover"/>
        </div>
        <div class="col-9">
            <div class="d-flex justify-content-between">
                <div class="col-10">
                    <p class="title">
                        {{music.title_short}}
                    </p>
                    <p class="artist">
                        {{music.artist.name}}
                    </p>
                </div>
                <div class="col-1">
                    <router-link :to="{ name: 'lyrics', params: { musicName: music.title_short, artistName: music.artist.name }}">More</router-link>
                </div>   
            </div>
            <div>
                <audio controls>
                    <source :src="music.preview" type="audio/mpeg"/>
                        Your browser does not support the audio element.
                </audio>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    props:["music"]
}
</script>
<style lang="scss" scoped>
    .music {
        background-color:#f8f9fa;
        color: #000;
        margin: 10px;
        display: flex;
        padding: 20px;
        
        img{
            max-height:150px;
        }
        p{
            text-align:left;
        }
        .title{
            font-size:16px;
            font-weight: 600;
        }
        .artist{
            font-size: 13px;
            color:lightslategray;

        }
        audio{
            width: 100%;
            height: 40px;
        }
    }
</style>
