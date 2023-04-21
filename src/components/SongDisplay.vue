<template>
    <div>

        <section class='player'>
            <h3 class='songs-title'>{{current.title}} - <span>{{current.artist}}</span></h3>

            <div id='control'>
                <button id='play' v-if='isplaying' @click="play">Play</button>
                <button id='next' v-else @click="next"></button>

            </div>

        </section>
     
       <section id='playlist'>
        
        <h3>The PlayList Section</h3>
        <button v-for='(songs, i) in songs' :key='i' @click='play(songs)'> {{songs.title}} --  {{songs.artist}}

        </button>
       
       
        </section>
       
    </div>
</template>

<script>
    export default {
        
        methods:{
            play(song) {
                if (typeof song !='undefined'){
                    this.current =song;

                    this.player.src = this.current.src;
                }
                this.player.play();
                this.isplaying = true;
            },

            next (){
                this.player.next();
            this.isplaying =false

                
            }
        },
   
   

        data() {

            return {
              isplaying: false,
              current: {},
              index: 0,
                songs: [
                    
                    {
                        title: 'sticky',
                        artist: 'Drake',
                        song_id: 'sticky',
                        image_url: 'https://www.youtube.com/watch?v=AnZcWgXZOKM&ab_channel=DrakeVEVO',

                    },

                    {
                        title: 'easy on me',
                        artist: 'Adele',
                        song_id: 'easy',
                        image_url: 'https://www.youtube.com/watch?v=U3ASj1L6_sY&ab_channel=AdeleVEVO',
                    },

                ],
                
                
            };
        },

        created(){
            this.current = this.songs[this.index];
        },
        
    };
</script>

<style lang="scss" scoped>

</style>

