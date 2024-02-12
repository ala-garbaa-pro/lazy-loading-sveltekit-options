<script lang="ts">
  export let src: string;
  export let alt: string;

  import { onMount } from "svelte";

  let loaded = false;
  let thisImage: HTMLImageElement;

  onMount(() => {
    thisImage.onload = () => {
      loaded = true;
    };
  });
</script>

<div style="width: 300px; height:500px;">
  <img {src} {alt} class:loaded bind:this={thisImage} loading="lazy" />
</div>

<style>
  img {
    height: 300px;
    width: 500px;
    opacity: 0;
    transition: opacity 1200ms ease-out;
  }
  img.loaded {
    opacity: 1;
  }
</style>
