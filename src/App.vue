<template>
  <div id="app">
      <div id="sidebar">
          <nav id="menu" class="box-menu">
              <a href="#">Create task</a>
              <a href="#">Active tasks</a>
              <a href="#">Closed tasks</a>
          </nav>
          <button class="toggle-menu">&times;</button>
      </div>
      <header class="box">
          <h2>Tasker</h2>
          <button class="toggle-menu">Menu</button>
      </header>
      <div id="content">
          <div class="box">
              <TaskList
                      v-bind:tasks="tasks"
                      v-bind:title="title"
              />
          </div>
          <footer class="box">
            footer
          </footer>
      </div>

<!--      <div class="ocean">-->
<!--        <div class="wave"></div>-->
<!--        <div class="wave"></div>-->
<!--      </div>-->
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
              { id: 4, text: 'Learn React', completed: false },
              { id: 5, text: 'Learn Test', completed: false },
              { id: 6, text: 'Learn Vue JS', completed: false },
              { id: 7, text: 'Learn Vue-CLI', completed: false },
              { id: 8, text: 'Learn Node JS', completed: false },
              { id: 9, text: 'Learn React', completed: false },
              { id: 10, text: 'Learn Test', completed: false },
              { id: 11, text: 'Learn Test', completed: false }
          ]
      }
  },
  components: {
    TaskList
  }
}
document.addEventListener('DOMContentLoaded', function(){
    const sidebar = document.getElementById('sidebar');
    for (const btn of [...document.querySelectorAll('.toggle-menu')]) {
        btn.addEventListener('click', (event) => {
            event.preventDefault();
            sidebar.classList.toggle('active')
        }
    )}
    /* eslint-disable no-console */
    //console.log(window.innerWidth);
    /* eslint-enable no-console */
});

</script>

<style>
    @import url('https://fonts.googleapis.com/css?family=Baloo+Bhai&display=swap');
    @import url('https://fonts.googleapis.com/css?family=Barlow:300,400&display=swap');

    html, body { height: 100%; }
    body {
        background:radial-gradient(ellipse at center, rgb(255, 254, 255) 0%, rgba(255,254,255,1) 35%, #e8ebeb 100%);
        display: flex;
        justify-content: center;
    }

    #app {
        display: grid;
        grid-template-columns: 1fr 2fr;
        grid-template-rows: minmax(100px, 250px) auto;
        grid-gap: 10px;
        width: 100%;
        max-width: 700px;
    }

    #sidebar {
        grid-row: 1/3;
        grid-column: 1/2;
        height: 100%;
    }

    #menu {
        position: sticky;
        top: 0;
    }

    header {
        grid-row: 1/2;
        text-align: center;
        font-family: 'Baloo Bhai', cursive;
    }
    header h2 {
        margin: 15px 0;
    }

    #menu > a{
        display: block;
        font-family: 'Baloo Bhai', cursive;
        text-decoration: none;
        color: #21eed2;
    }

    #content {
        grid-row: 2/3;
        grid-column: 2/3;
    }

    .toggle-menu {
        display: none;
    }

    .box, .box-menu {
        background: #FFF;
        font-size: 20px;
        /*max-width: 20em;*/
        padding: 0.5em 1em;
        box-shadow: 0 5px 30px rgba(0, 0, 0, 0.2);
    }

    /* OCEAN */

    .ocean {
    z-index: -1000;
    height: 5%;
    width:100%;
    position:absolute;
    bottom:0;
    left:0;
    background: #015871;
    }

    .ocean-bottom {
      position:absolute;
      height: 100%;
      background-color: #015871;
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

    @media (max-width: 575.98px) {
        #app {
            grid-gap: 0;
        }
        header {
            grid-column: 1/3;
            position: relative;
        }
        header .toggle-menu {
            position: absolute;
            right: 25px;
            top: 40px;
        }

        #content {
            grid-row: 3/4;
            grid-column: 1/3;
        }
        #sidebar {
            grid-row: 1/4;
            grid-column: 1/3;
            background: linear-gradient(155deg, #27FDC7, #0FC0F5);
            height: 100%;
            z-index: 10;
            padding: 20px;
            transition: transform .15s ease-out;
            transform-origin: left center;
            transform: scaleX(0);
        }
        #sidebar.active {
            transform: scaleX(1);
            position: relative;
        }

        #sidebar .toggle-menu {
            position: absolute;
            right: 25px;
            top: 12px;
            font-size: 60px;
            color: white;
        }

        .toggle-menu {
            display: block;
        }

        #menu > a{
            color: white;
            font-size: 35px;
        }

        .box-menu {
            background: none;
            box-shadow: none;
        }

        .box {
            max-width: none;
        }
    }

    @media (max-width: 767.98px) {

    }

    @media (max-width: 991.98px) {

    }

    @media (max-width: 1199.98px) {

    }

    @media (min-width: 1200px) {

    }
</style>
