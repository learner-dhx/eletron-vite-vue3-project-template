<template>
  <!-- <ul class="versions">
    <li class="electron-version">Electron v{{ versions.electron }}</li>
    <li class="chrome-version">Chromium v{{ versions.chrome }}</li>
    <li class="node-version">Node v{{ versions.node }}</li>
    <li class="v8-version">V8 v{{ versions.v8 }}</li>
  </ul> -->
  <div>
      <input type="text" id="title" ref="title">
      <button id="btn" @click="changeTitle">changeTitle</button>
  </div>
</template>
<script setup>
import { reactive,ref } from 'vue'
const ipcRenderer = window.electron.ipcRenderer
const title = ref()
const versions = reactive({ ...window.electron.process.versions })
// console.log(w)

function changeTitle(){
  ipcRenderer.send('change-title', title.value.value )
}
</script>