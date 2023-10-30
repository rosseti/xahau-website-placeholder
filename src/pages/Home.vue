<template>
  <div class="vertline" style="left:10%; "></div>
  <div class="horline" style="top:51%"></div>

  <div class="container home" data-theme="dark">
    <div class="grid">

      <div class="header">
          <img class="logo animate fade" src="/images/logo-light.svg" />
      </div>

      <div class="main animate fade delay-8">
          <h1><span>The <b>Smart Contract Sidechain</b></span> <span>for the XRPL Ecosystem <small>- Xahau Launch Alliance, 2023</small></span></h1>
          <a href="Xahau-Whitepaper.pdf" role="button" target="_blank" class="contrast whitepaper">
            Read the whitepaper&nbsp; <FileDigit :size="28" :stroke-width="2.5" />
          </a>
      </div>

      <div class="developers">
        <div class="vertline" style="position:fixed; margin-top:-8rem; right:8%; "></div>
        <div class="devbox animate fade delay-10">
            <hgroup>
                <h4>Developer?</h4>
                <p><strong style="display: inline-block; margin-bottom: 5px; color: var(--yellow);">Hooks are the native smart contracts on the Xahau network.</strong><br />Checkout our docs and tools.</p>
            </hgroup>
            <a style="margin-bottom: 8px;" href="https://hooks-builder.xrpl.org" role="button" class="primary btnsm">Hooks builder <Hammer :size="20" :stroke-width="2.5" /></a>
            <a style="margin-bottom: 8px;" href="https://xrpl-hooks.readme.io" role="button" class="primary btnsm">Hooks docs <FileCode :size="20" :stroke-width="2.5" /></a>
            <a style="margin-bottom: 8px;" href="https://hooks-testnet.xrpl-labs.com" role="button" class="primary btnsm">Hooks testnet <FlaskConical :size="18" :stroke-width="2.5" /></a>
        </div>
      </div>

      <div class="horline" style="bottom:100px;"></div>
      <div class="footer animate slide delay-12">
          <a href="https://github.com/Xahau" role="button" class="primary btnsm">Github <Github :size="18" :stroke-width="2.5" /></a>
          <!-- <a href="#" role="button" class="primary btnsm">Blog <Newspaper :size="18" :stroke-width="2.5" /></a> -->
          <a href="https://x.com/XahauNetwork" role="button" class="primary btnsm"><Twitter :size="18" :stroke-width="2.5" /> / <X :size="18" :stroke-width="2.5" /></a>
          <a href="https://github.com/Xahau/Graphics" role="button" class="primary btnsm">Download Brand Assets <DownloadCloud :size="18" :stroke-width="2.5" /></a>

          <!-- <small>Who...?</small> -->
      </div>
    </div>
  </div>

  <div class="backgroundfade"></div>

  <TresCanvas
    alpha
    window-size
    class="animate blur delay-3"
    >
    <TresPerspectiveCamera
      :position="[1.1, -0.5, 4.6]"
      :near="0.1"
      :far="1000"
    />

    <OrbitControls
      :autoRotate="true"
      :autoRotateSpeed="0.4"
      :enableRotate="false"
      :enablePan="false"
      :enableZoom="false"
      />

    <TresGroup :position="[0,-2.3,0]">
      <TresAmbientLight color="#ffffff" intensity="0.6" />

      <TresDirectionalLight color="#FFFD57" intensity="0.5" :position="[0, 7, 0]" />
      <TresPointLight color="#8C9A9D" :intensity="25" :position="[0, 5, 5]" />
      <TresPointLight color="#FFFD57" :intensity="30" :position="[0, 3, -5]" />

      <Suspense>
        <primitive :object="nodes.icon" />
      </Suspense>

      <!-- <TresGridHelper :args="[20, 20]" /> -->
    </TresGroup>

  </TresCanvas>
</template>



<script setup>

import { onMounted } from 'vue';
import { TresCanvas } from '@tresjs/core';
import { useGLTF, OrbitControls, vLightHelper } from '@tresjs/cientos'

const { nodes } = await useGLTF('/models/x.gltf', { draco: true })

import { FileDigit, FileCode, FlaskConical, Hammer, Github, Newspaper, Twitter, X, DownloadCloud } from 'lucide-vue-next';


onMounted(() => {
  // Set metalness to zero for amientlight
  nodes.icon.material.metalness = 0
})

</script>


<style lang="scss">

.vertline {
  width:1px; height:100%;
  position: fixed;
  z-index: 1;
  background:rgba(#ffffff,0.1);
}
.horline {
  height:1px; width:100%;
  position: fixed;
  left:0;
  background:rgba(#ffffff,0.1);
  z-index:1;
}

div.backgroundfade {
  width:50%; height:200px;
  border-radius: 100%;
  transform: translate(50%,200px);
  position: fixed;
  bottom:0;
  -webkit-box-shadow:0px 0px 170px 223px rgba(160,255,87,0.05);
  -moz-box-shadow: 0px 0px 170px 223px rgba(160,255,87,0.05);
  box-shadow: 0px 0px 170px 223px rgba(160,255,87,0.05);
}


div.container , div.container-fluid {
  position: relative;
  z-index: 10;
  > .grid {
    height: 100%;
    height: 100svh;
  }
}

canvas {
  z-index:5;
}

/*
//
// Grid
//
*/

article.alert {
  margin:0;
  padding:0.5rem;
  font-size:0.7rem;
  border-radius: 0;
  text-align: center;
  position: absolute;
  left:0;
  width:100%;
  z-index: 11;
  a { color:#fff; }
}

div.grid {
  display: grid;
  grid-template-rows:200px 4fr 4fr 100px;

  > * {
    display: grid;
  }
  div.header {
    align-content: center;
  }
  div.main {
    padding:0 0 2rem 0;
    justify-items: start;
    align-content: start;
    h1 {
      font-size:3rem;
      line-height:2.9rem;
      letter-spacing: -1.2px;
      margin-bottom:1rem;
      b { color:var(--yellow);}
      span { display:inline-block; }
      small { font-weight: 400; font-size:0.8rem; vertical-align: middle; margin-left:0.5rem;  letter-spacing: normal;}
    }
  }
  div.developers {
    justify-items: end;
    align-content: start;
    > div.devbox {
      padding:1rem;
      background:rgba(#909090,0.25);
      border-radius: 0.3rem;
      margin-bottom:3rem;
      p {color:#fff; font-size:0.9rem; }

      a { margin:0 0.5rem 0 0; background:var(--purple-light); border-color:var(--purple-light); color:var(--purple); }
    }
  }
  div.footer {
    grid-template-columns: auto auto auto auto auto;
    padding:1rem 0;
    justify-content: start;
    align-content: center;
    align-items:center;
    a { margin:0 0.5rem 0 0; color:var(--green); }
    small {  vertical-align: middle; font-weight:bold; font-size:0.6rem; margin-left:1rem;  }

  }
}

</style>


