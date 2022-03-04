<template>
  <div class="about">
    <h1>This is an about page</h1>
    <button type="button" @click="onYouTubeIframeAPIReady">play</button>
    <iframe ref="playerPosition" src="https://www.youtube.com/embed/8MG--WuNW1Y?wmode=opaque&autohide=1&autoplay=1&mute=0&loop=1&playlist=8MG--WuNW1Y" frameborder="0"></iframe>
  </div>
</template>

<script>
import player from 'youtube-player'

export default {
  data () {
    return {
      player: {}
    }
  },
  methods: {
    onYouTubeIframeAPIReady () {
      this.player = player(this.$refs[this.playerPosition], {
        playerVars: {
          rel: 0,
          autoplay: 1,
          loop: 1,
          frameborder: 0,
          enablejsapi: 1,
          controls: 0,
          autohide: 0,
          modestbranding: 1
        }
      })
      console.log(this.player)
    },
    playVideo () {
      this.player.playVideo()
    }
  },
  mounted () {
    this.player = player(this.$refs.playerPosition)
  }
}
</script>
