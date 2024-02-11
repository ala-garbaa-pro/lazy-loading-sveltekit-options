<script lang="ts">
  import { listImagesSources } from "$lib/listImagesSources";
  import { inview } from "svelte-inview";
  import type { ObserverEventDetails, Options } from "svelte-inview";

  let isInView: boolean;
  const options: Options = {
    rootMargin: "50px",
    unobserveOnEnter: true,
  };

  const handleChange = ({ detail }: CustomEvent<ObserverEventDetails>) =>
    (isInView = detail.inView);
</script>

<h1>Lazy Loading Images</h1>

<p>
  Svelte Inview lets you easily lazy load images. For a better UX we can pass a
  rootMargin="50px" props, so the image will be loaded when scroll is 50px
  before the viewport. After it appears in the viewport, you don't want to
  observe it anymore, hence the unobserveOnEnter props set to true.
</p>
<hr />

{#each listImagesSources as src, i (src)}
  <div use:inview={options} on:inview_change={handleChange}>
    {#if isInView}
      <div style="height:500px; width:100%; background-color:tomato">
        <p>{src}</p>
        <pre>{JSON.stringify(isInView, null, 2)}</pre>
      </div>
      <!-- <img {src} alt={`You can find this image on URL: ${src}`} /> -->
    {:else}
      <div class="placeholder" />
    {/if}
  </div>
{/each}
