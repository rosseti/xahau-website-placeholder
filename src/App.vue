<!-- <nav>
  <router-link to="/">Home</router-link> | <router-link to="/about">About</router-link>
</nav>
<main>
  <router-view />
</main> -->

<template>
  <Suspense>
    <router-view />
  </Suspense>
</template>

<style lang="scss">
  @import "/css/pico.slim.css";
  @import "/css/animate.css";
  @import url('https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600;700;800&display=swap');
  :root {
    --green: #0F2328;
    // --green: #0E0143;
    --yellow: #FFFD57;
    --purple: #8612EB;
    --purple-light: #ECE3F4;
  }
  a[role="button"] {
    font-weight: 800;
    &:hover {
      // transform: scale(1.05);
      transform: scale(0.95);
      transition: all ease-in-out 75ms;
    }
  }
  .btnsm {
    font-weight: 600 !important;
  }

  svg.lucide {
    vertical-align: top;
    // margin: 0 0 0 0.5rem;
  }

  // MOBILE
  @media (max-width: 576px) {
    canvas {
      opacity:0.5;
    }
    .btnsm {
      // width:100%; display: block;
      font-size:0.9rem;
      margin-bottom:1rem !important;
    }

    div.grid {
      height:auto !important;
      grid-template-rows:150px 4fr 4fr 100px !important;
      // grid-template-rows: auto auto auto auto !important;
    }
    div.grid div.header {
      justify-items: center !important;

    }
    div.grid div.main {
      justify-items: center !important;
      margin-bottom:3rem;
      h1 {
        text-align: center; width:100%; font-size: 2.6rem !important;
        b, small {display: block;}
      }
      .whitepaper {
        font-size:1.2rem;
      }
    }
    div.grid .developers {
      div.devbox {
        width:100%;
      }
    }
    div.grid div.footer {
      width:100%; height:300px;
      grid-template-columns: none !important;
      grid-template-rows: auto auto auto  !important;
      justify-content: center !important;
      align-content: center;
      align-items: center;

      .btnsm {
        width:100%; display: block;
        margin-bottom:1rem !important;
      }
      small {
        font-size:0.9rem !important;
        text-align: center;
        height:60px;
      }
    }

  }
  @media (min-width: 576px) {

    .btnsm {
      font-size:0.7rem;
      padding:0.3rem 0.6rem;
    }
  }
  // .btnsm {
  //   padding:0.3rem 0.6rem;
  //   font-size:0.6rem;
  //   font-weight: bold;
  // }

  @media (min-width: 1600px) {
    .container {
      max-width: 1340px;
    }
  }

  html {
    background: var(--green);
    // background: radial-gradient(ellipse at center bottom, rgba(161,255,87,100%) -100%, rgba(15,35,40,100%) 100%);
  }
  body {
    margin: 0; padding:0;
    font-family: 'Poppins';
    color:#fff;
    // background: radial-gradient(ellipse at center bottom, rgba(161,255,87,100%) -50%, rgba(15,35,40,100%) 100%);
    // border:2px solid red;
  }
  #app {
    height:100svh;
    width:100svw;
  }
</style>
