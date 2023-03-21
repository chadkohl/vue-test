<script setup>
import * as THREE from 'three';

// init

const camera = new THREE.PerspectiveCamera( 70, window.innerWidth / window.innerHeight, 1, 1000 );
camera.position.z = 50;

const scene = new THREE.Scene();

const geometry = new THREE.TorusGeometry( 10, 3, 16, 100 );
const material = new THREE.MeshPhysicalMaterial({ color: 0xD4AF37, metalness: 0.25, clearcoat: 1});

const mesh = new THREE.Mesh( geometry, material );
scene.add( mesh );

const renderer = new THREE.WebGLRenderer( { antialias: true } );
renderer.setSize( window.innerWidth, window.innerHeight );
renderer.setAnimationLoop( animation );
document.body.appendChild( renderer.domElement );

{
  const color = 0xFFFFFF;
  const intensity = 1;
  const light = new THREE.DirectionalLight(color, intensity);
  light.position.set(0, 2, 1);
  scene.add(light);
}

// animation

function animation( time ) {

	mesh.rotation.x = time / 10000;
	mesh.rotation.y = time / 5000;

	renderer.render( scene, camera );

}
</script>

<template>
  
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
