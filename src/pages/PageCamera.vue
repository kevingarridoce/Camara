<template>
  <q-page class="flex flex-center">
    
    <div class="camera-frame q-pa-md">
        <video 
        v-show="!imageCaptured"
        ref="video"
        class="full-width"
        autoplay
        />
        <canvas
            v-show="imageCaptured"
            ref="canvas"
            class="full-width"
            height="240"
        />

        
    </div>
<div class="text-center q-pa-md">
    <q-btn @click="captureImage" round color="black" icon="camera"  size="lg"/>
</div>
<div class="row justify-center text-center q-mt-lg">
    <q-btn  color="primary" icon="save" label="guardar" size="lg"/>
</div>


  </q-page>
</template>

<script>
import{uid} from 'quasar'
require('md-gum-polyfill')
export default {
  name: 'PageCamera',
  data(){
      return{
          post:{
              photo:null
          },
          imageCaptured: false
      }
      
  },
    methods:{
       initCamera(){
           navigator.mediaDevices.getUserMedia({
               video: true
           }).then(stream => {
               this.$refs.video.srcObject = stream
           })
       },
        captureImage(){
          let video=  this.$refs.video
          let canvas=  this.$refs.canvas
          canvas.width = video.getBoundingClientRect().width
          canvas.height = video.getBoundingClientRect().height
          let context = canvas.getContext('2d')
          context.drawImage(video, 0, 0, canvas.width, canvas.height)
          this.imageCaptured = true
          this.post.photo= canvas.toDataURL()
          this.disableCamera()
        },
        disableCamera(){
            this.$refs.video.srcObject.getVideoTracks().forEach(track => {
                track.stop()
            })
        }
    },
    
    mounted(){
        this.initCamera()
    },
    beforeDestroy(){
        if(this.hasCameraSupport){
            this.disableCamera()
        }
    }
}
</script>
<style lang="sass">
.camera-frame
    border: 2px solid $grey-10
    border-radius: 10px

</style>
