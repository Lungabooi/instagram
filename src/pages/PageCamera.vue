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
    v-if="hasCameraSupport"
    @click="captureImage()"
    color="grey-10"
    icon="eva-camera"
    size="lg"
    round >

    </q-btn>
    <q-file
    v-else
    v-model="imageUpload"
    label="Choose an image" 
    outlined> 
    <template
     v-slot:prepend
     >
    <q-icon
     name="eva-attach-outlined"
     ></q-icon></template>

 </q-file>
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

import { nextTick, prependListener } from 'process'
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
        imageCaptured: false,
        imageUpload: [],
        hasCameraSupport : true
      }
    },
    methods: {
      initCamera() {
        navigator.mediaDevices.getUserMedia ( {
        video: true
     }). then (stream => {
        this.$refs.video.srcObject = stream
     }).catch(error => {
      this.hasCameraSupport = false
     })
      },
      captureImage() {
        let video = this.$refs.video
        let canvas = this.$refs.canvas
        canvas.width = video.getBoundingClientRect().width
        canvas.height = video.getBoundingClientRect().height
        let context = canvas.getContext('2d')
        context.drawImage(video, 0, 0, canvas.width, canvas.height)
       this.imageCaptured = true 
      this.post.photo = this.dataURItoBlob(canvas.toDataURL())},
      dataURItoBlob(dataURI) {
  // convert base64 to raw binary data held in a string
  // doesn't handle URLEncoded DataURIs - see SO answer #6850276 for code that does this
  var byteString = atob(dataURI.split(',')[1]);

  // separate out the mime component
  var mimeString = dataURI.split(',')[0].split(':')[1].split(';')[0]

  // write the bytes of the string to an ArrayBuffer
  var ab = new ArrayBuffer(byteString.length);

  // create a view into the buffer
  var ia = new Uint8Array(ab);

  // set the bytes of the buffer to the correct values
  for (var i = 0; i < byteString.length; i++) {
      ia[i] = byteString.charCodeAt(i);
  }

  // write the ArrayBuffer to a blob, and you're done
  var blob = new Blob([ab], {type: mimeString});
  return blob;

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