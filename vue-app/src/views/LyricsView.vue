<template>
    <div class="lyric">
        <div class=" container">
                <div class="text-left lyric__header">
                    <h3 class = 'title'>{{musicName}}</h3>
                    <h2 class = 'artist'>Song by {{artistName}} : </h2>
                </div>
                <div class="lyric__body">
                    <pre>{{lyric}}</pre>
                </div>
            </div>
    </div>
</template>
<script>
export default {
    data(){
        return {
            musicName:this.$route.params.musicName,
            artistName:this.$route.params.artistName,
            lyric:''
        }
    },
    created(){
        this.getLyric()
    },
    methods:{
        getLyric(){
            console.log('created')
            fetch(`https://api.lyrics.ovh/v1/${this.artistName}/${this.musicName}`)
        .then(res => res.json())
        .then(
            (result) => {
                console.log(result)
                result.lyrics ? 
            this.lyric = result.lyrics : result.error
        },
            (error) => {
                let notFound = error.error;
                this.lyric = notFound
            }
        );
        }
    }
    
}
</script>
<style lang="scss">
    .lyric{
    padding:10px;
    text-align: left;
    background: darkgray;
    .lyric__header{

        .artist{
            font-size: 12px;
            color:white;
            padding-left: 5px;
        }
    
    }
    .lyric__body{
        text-align: justify;
        margin-top:20px
    }
}
</style>