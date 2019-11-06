<template>
  <div id="app">
      <TaskList
          v-bind:tasks="tasks"
          v-bind:title="title"
      />
      <div class="ocean">
        <div class="wave"></div>
        <div class="wave"></div>
      </div>
  </div>
</template>

<script>

import TaskList from "./components/TaskList";

export default {

  name: 'app',
  data() {
      return {
          title: 'Web developing',
          tasks: [
              { id: 1, text: 'Learn Vue JS', completed: false },
              { id: 2, text: 'Learn Vue-CLI', completed: false },
              { id: 3, text: 'Learn Node JS', completed: false },
              { id: 4, text: 'Learn React', completed: false }
          ]
      }
  },
  components: {
    TaskList
  }
}
</script>

<style>
  html, body { height: 100%; }
  body {
    background:radial-gradient(ellipse at center, rgb(255, 254, 255) 0%, rgba(255,254,255,1) 35%, #e8ebeb 100%);
    overflow: hidden;
  }

  .ocean {
    height: 5%;
    width:100%;
    position:absolute;
    bottom:0;
    left:0;
    background: #015871;
  }

  .wave {
    background: url(https://s3-us-west-2.amazonaws.com/s.cdpn.io/85486/wave.svg) repeat-x;
    position: absolute;
    top: -198px;
    width: 6400px;
    height: 198px;
    animation: wave 7s cubic-bezier( 0.36, 0.45, 0.63, 0.53) infinite;
    transform: translate3d(0, 0, 0);
  }

  .wave:nth-of-type(2) {
    top: -175px;
    animation: wave 7s cubic-bezier( 0.36, 0.45, 0.63, 0.53) -.125s infinite, swell 7s ease -1.25s infinite;
    opacity: 1;
  }

  @keyframes wave {
    0% {
      margin-left: 0;
    }
    100% {
      margin-left: -1600px;
    }
  }

  @keyframes swell {
    0%, 100% {
      transform: translate3d(0,-25px,0);
    }
    50% {
      transform: translate3d(0,5px,0);
    }
  }
</style>
