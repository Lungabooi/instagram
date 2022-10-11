<template>
  <q-page class="constrain-more q-pa-md" >
   <div class="camera-frame q-pa-md">
    <video
    ref="video"
    class="full-width"
    autoplay></video>
  
   </div>
   <div class="text-center q-pa-md">
    <q-btn
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
        }
      }
    },
    methods: {
      initCamera() {
        navigator.mediaDevices.getUserMedia ( {
      video: true
     }). then ( stream => {
        this.$refs.video.srcObject = stream
     })
      }
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