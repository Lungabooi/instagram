<template>
  <q-page class="constrain-more q-pa-md" >
   <div class="camera-frame q-pa-md">
    <video
    v-show='!imageCaptured'
    ref="video"
    class="full-width"
    autoplay
/>
<canvas 
  v-show= 'imageCaptured'
    ref='canvas'
    class="full-width"
    height="240px"


    /> 
  
   </div>
   <div class="text-center q-pa-md">
    <q-btn
    @click="captureImage()"
    color="grey-10"
    icon="eva-camera"
    size="lg"
    round >

    </q-btn>
    <div class="div row justify-center q-ma-md">
      <q-input
      v-model="post.caption"
      label="Caption"
      class="col  col-sm-6"
      >
    </q-input>
    </div>
    <div class="div row justify-center q-ma-md">
      <q-input
      v-model="post.location"
      label="Location"
      class="col col-sm-6"
      >
      

      <template v-slot:append>
        <q-btn 
        rounded 
        flat 
        icon="eva-navigation-2-outline">
      </q-btn>
      </template>
    </q-input>
    </div>
    <div 
    class="row justify-center
     q-ma-md">  
     <q-btn 
     unelevated 
     rounded 
     color="primary" 
    label="Post Image" /></div>
   </div>
  

  </q-page>
</template>

<script>

import { nextTick } from 'process'
import { openURL, uid } from 'quasar'
export default {
    name: 'PageCamera',
    data(){
      return {
        post:{
          id: uid(),
          caption: '',
          location:'',
          photo:'null',
          date: Date.now()
        },
        imageCaptured: false
      }
    },
    methods: {
      initCamera() {
        navigator.mediaDevices.getUserMedia ( {
        video: true
     }). then (stream => {
        this.$refs.video.srcObject = stream
     })
      },
      captureImage() {
        let video = this.$refs.video
        let canvas = this.$refs.canvas
        canvas.width = video.getBoundingClientRect().width
        canvas.height = video.getBoundingClientRect().height
        let context = canvas.getContext('2d')
        context.drawImage(video, 0, 0, canvas.width, canvas.height)
       this.imageCaptured = true }
    },
    mounted() {
     this.initCamera()
    }
}
</script>

<style lang="sass">
.camera-frame
  border: 2px solid $grey-10
  border-radius: 10px

</style>