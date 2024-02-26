<script setup>
import { ref } from 'vue';
import "../aframe/pavement.js";
import "../aframe/clickable.js";
import "../aframe/teleport-camera-rig.js";
  

  import TheCameraRig from './TheCameraRig.vue';
  import TheMainRoom from './TheMainRoom.vue';
  //import TheLifeCubeRoom from './TheLifeCubeRoom.vue';

  

  defineProps({
    scale: Number,
    overlaySelector: String,
  });

  const allAssetsLoaded = ref(false);
</script>

<template>
  <a-scene 
  wfog="type: exponential; color: #FFF; near:500; far: 700; density:0.003 "
    background="color: black;"
    :webxr="`
      requiredFeatures: local-floor;
      referenceSpaceType: local-floor;
      optionalFeatures: dom-overlay;
      doverlayElement: ${overlaySelector};
    `"
    xr-mode-ui="XRMode: xr"
    physx="
      autoLoad: true;
      delay: 1000;
      useDefaultScene: false;
      wasmUrl: lib/physx.release.wasm;
    "
    stats
  >

    <a-assets @loaded="allAssetsLoaded = true">
      <!--
        Title: VR Gallery
        Model source: https://sketchfab.com/3d-models/vr-gallery-1ac32ed62fdf424498acc146fad31f7e
        Model author: https://sketchfab.com/mvrc.art (Maxim Mavrichev)
        Model license: CC BY 4.0 ( https://creativecommons.org/licenses/by/4.0/ )
      -->
      <a-asset-item id="room" src="assets/vr_gallery.glb"></a-asset-item>
      <!--
        Title: 3D Gallery for VR projects
        Model source: https://sketchfab.com/3d-models/3d-gallery-for-vr-projects-68f77ed8558c4bd59e0a13e2cc9d1fd1
        Model author: https://sketchfab.com/tekuto1s (tekuto1s)
        Model license: CC BY 4.0 ( https://creativecommons.org/licenses/by/4.0/ )
      -->
      <a-asset-item id="physic-room" src="assets/3d_gallery_for_vr_projects.glb"></a-asset-item>
      <a-asset-item id="sound-1" response-type="arraybuffer" src="assets/sound1.mp3" preload="auto"></a-asset-item>
      <img id="room-physic-out-texture" :src="`assets/main-room-from-physic-room.png`">
      <img id="room-gol-out-texture" :src="`assets/main-room-from-gol-room.png`">
      <img id="room-physic-texture" :src="`assets/physicRoom.png`">

<!--Mes assets-->
      <a-asset-item id="canoe" src="assets/canoe2.glb"></a-asset-item>
      <a-asset-item id="lake_scene" src="assets/lake_scene.glb"></a-asset-item>
      <a-asset-item id="wooden_boat" src="assets/wooden_boat.glb"></a-asset-item>
      <a-asset-item id="lake_scene2" src="assets/lake_scene2.glb"></a-asset-item>
      <a-asset-item id="lake" src="assets/lake.glb"></a-asset-item>
      <a-asset-item id="boatDock" src="assets/boat_dock.glb"></a-asset-item>
      <a-asset-item id="woodenSign" src="assets/wooden_sign.glb"></a-asset-item>
    </a-assets>

   <template v-if="allAssetsLoaded">
    <!-- <TheMainRoom :scale="scale" />
    <TheLifeCubeRoom />
    <ThePhysicRoom />
    <a-ocean color="lightblue" width="10" depth="10" density="20" speed="2"></a-ocean>
    <a-ocean color="lightblue" width="10" depth="10" density="10" speed="2"></a-ocean>
    <a-sky color="white"></a-sky>
    <a-entity light="type: ambient; color: white"></a-entity>
    <a-entity pavement ></a-entity> -->
     <!-- <a-entity 
      gltf-model="#lake_scene"
      position="0 -10 0"
      scale="0.1 0.1 0.1"
     
    ></a-entity> -->


     <!-- <a-entity 
      gltf-model="#canoe"
      position="4 0.4 0"
      scale="0.03 0.03 0.03"
      rotation="0 180 0"
    ></a-entity> -->

    <!--Environnement-->
    <a-entity light="type: ambient; color: white"></a-entity>
    <a-sky color="lightblue"></a-sky>
    
    <a-ocean color="#478a7e" width="1000" depth="1000" density="90" speed="2" position="0 -1 0"></a-ocean>
    <a-ocean color="#478a7e" width="1000" depth="1000" density="80" speed="2" position="0 -1 0"></a-ocean>


    <a-box color="blue" ></a-box>

    <a-entity 
      gltf-model="#lake_scene2"
      position="-23 0 -45"
      scale="0.1 0.1 0.1"
      ></a-entity>

      <a-entity 
      gltf-model="#boatDock"
      position="-0.8 -1 -4"
      scale="7 7 7"
      rotation="0 15 0"
    ></a-entity>

    
    <a-entity 
      gltf-model="#boatDock"
      position="-45 -1 -68"
      scale="7 7 7"
      rotation="0 170 0"
    ></a-entity>



    <a-entity
    gltf-model="#woodenSign"
    scale="0.004 0.004 0.004"
    position="-2 0.75 -6.5"
    rotation="0 -45 0"
    clickable 
    teleport-camera-rig="x:.1; y: 0; z: -5"
    ></a-entity>


    <!--Bateau-->
    <a-entity
      gltf-model="#wooden_boat"
      position="0.1 -0.5 -6.5"
      dscale="0.8 0.8 0.8"
      rotation="0 190 0"
      
    
    ></a-entity>

  
    </template> 




    <TheCameraRig
    position="-2.5 1 -1"/>

   

  </a-scene>
</template>