<template>
    <div class="container-xxl">
      <div class="row justify-content-center">
        <div class="col-12 col-auto mt-2 player">
          <video id="video" ref="video" src="../assets/lofi.mp4" muted></video>
          <h2 class="player-title text-light">Música para programar</h2>
          <div class="player-actions">
            <!-- <input type="hidden" ref="durationVideo" v-model="video.duration"> -->
            <button class="button btn" id="backward" @click="onBackward">
              <vue-feather type="skip-back" title="Retroceder 10 segundos" />    
            </button>
            <button class="button btn" v-if="!hidden" ref="play" @click="onPlay">
              <vue-feather type="play" title="Reproducir" />
            </button>
            <button class="button btn" v-else @click="onPause">
              <vue-feather type="pause" title="Pausar" />
            </button>
            <button class="button btn" id="forward" @click="onForward">
              <vue-feather type="fast-forward" title="Adelantar 10 segundos" />
            </button>
          </div>
          <div class="player-progress">
            <input class="form-range" type="range" ref="progress" min=0 value="0" step="1">
          </div>
        </div>
      </div>
    </div>
</template>

<script>
    // TODO: DONE ICONS FOR BUTTONS 🚀🚀 & CONTINUE WITH COURSE JEJE
    /* import { RewindIcon, SkipForwardIcon, FastForwardIcon } from 'vue-feather' */
    import { ref, onMounted  } from 'vue';
    import VueFeather from 'vue-feather';

    export default {
      name: 'VideoPlayer',
      components: {
        VueFeather
      },
      setup () {
        const hidden   = ref(false)
        const progress = ref(null)
        const video    = ref(null)
        const duration = ref(null)

        const onBackward = () => {
          video.value.currentTime = video.value.currentTime - 10;
        }
        const onPlay = () => {
          video.value.play()
          hidden.value = true

          // save duration of video
          duration.value = video.value.duration;
          progress.value.max = duration.value;

        }
        const onPause = () => {
          video.value.pause()
          hidden.value = false
        }
        const onForward = () => {
          video.value.currentTime = video.value.currentTime + 10;
        }
        const onLoaded = () => {
          progress.value = video.value.currentTime;
          console.log(video.value.currentTime);
        
        }

        onMounted ( () => {
          console.log('Welcome to my VideoPlayer | Craftianos 2022 🧙‍♂️🚀');
          onLoaded()
        })

        return {
          hidden,
          progress,
          video,
          onBackward,
          onPlay,
          onPause,
          onForward
        }
      },
    }
</script>

<style scoped>
    .wrapper {
      max-inline-size: 900px;
      margin: auto;
    }

    .player {
      margin-block-start: 100px;
      position: relative;
    }

    .player video {
      inline-size: 100%;
      aspect-ratio: 16/9;
      vertical-align: middle;
    }

    .player-title {
      position: absolute;
      inset-block-start: 0;
      inset-inline-start: 20px;
    }

    .player-actions {
      position: absolute;
      inset: 0px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .player-progress {
      position: absolute;
      inset-block-end: 0;
      inset-inline: 0;
      display: flex;
      padding: 20px;
    }

    .player-progress input {
      flex: 1;
    }

    .btn {
      color: #fff;
      cursor: pointer;
    }
</style>