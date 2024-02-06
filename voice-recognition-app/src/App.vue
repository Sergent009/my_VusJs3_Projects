<template>
<div class="app">
  <button class="mic" @click="ToggleMic">Record</button>
  <div class="transcript" v-text="transcript"></div>
</div>
</template>

<script>
import {ref, onMounted} from 'vue'

export default {
  name: 'App',

  setup(){
    const transcript = ref('')
    const isRecording = ref(false)

    const recognation = window.SpeechRecognition || window.webkitSpeechRecognition

    // sr = speech recognation.
    const sr = new recognation()


  onMounted(() => {
    sr.continous = true
    sr.interimResult = true

    sr.onstart = () => {
      console.log('SR started')
      isRecording.value = true
    }

    sr.onend = () => {
      console.log('SR stopped')
      isRecording.value = false
    }

    sr.onresult = (evt) => {
      const t = Array.from(evt.results)
                .map(result => result[0])
                .map(result => result.transcript)
                .join('')

      transcript.value = t
    }
  })

  const ToggleMic = () => {
    if(isRecording.value){
      sr.stop()
    }
    else{
      sr.start()
    }
  }

  return{
    ToggleMic,
    onMounted,
    transcript
  }
 },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Pacifico&display=swap');

*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Pacifico', cursive;
}

body{
  background: rgb(26, 9, 26);
  color: #fff;
}

.mic{
  font-size: 23px;
  padding: 5px 30px;
  border: 3px solid white;
  border-radius: 5px;
}
.mic:hover{
  color: #fff;
  background:  rgb(26, 9, 26);
}
</style>
