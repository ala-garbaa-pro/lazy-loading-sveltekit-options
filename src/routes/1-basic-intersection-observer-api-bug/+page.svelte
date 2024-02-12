<script lang="ts">
  import { listImagesSources } from "$lib/listImagesSources";

  import ImageLoader from "./components/ImageLoader.svelte";
</script>

<h1>Intersection Observer API</h1>

<mark
  >Not as I expected, because when I loaded the page for the first time, I saw
  on the network tab of the browser that 5 images were loaded, but on my
  viewport, I only see two images</mark
>
{#each listImagesSources as src, i (src)}
  <ImageLoader {src} alt={`You can find this image N${i} on URL: ${src}`} />
{/each}
