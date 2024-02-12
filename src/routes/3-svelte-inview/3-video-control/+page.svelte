<script lang="ts">
  import { listImagesSources } from "$lib/listImagesSources";
  import { inview } from "svelte-inview";
  import type { ObserverEventDetails, Options } from "svelte-inview";
  import { fade } from "svelte/transition";

  type lazyloadingImages = {
    src: string;
    isInView: boolean;
  };

  const images: lazyloadingImages[] = listImagesSources.map((image) => ({
    src: image,
    isInView: false,
  }));

  const options: Options = {
    rootMargin: "50px",
    unobserveOnEnter: true,
  };

  const handleChange = (
    { detail }: CustomEvent<ObserverEventDetails>,
    i: number
  ) => (images[i].isInView = detail.inView);
</script>

<h1>Lazy Loading Images</h1>

<p>
  Svelte Inview lets you easily lazy load images. For a better UX we can pass a
  rootMargin="50px" props, so the image will be loaded when scroll is 50px
  before the viewport. After it appears in the viewport, you don't want to
  observe it anymore, hence the unobserveOnEnter props set to true.
</p>
<hr />

{#each images as { src, isInView }, i (src)}
  <div
    style="height:340px; width:512px; background-color:#123; margin-bottom: 50px;"
    use:inview={options}
    on:inview_change={(d) => handleChange(d, i)}
  >
    {#if isInView}
      <img
        in:fade={{ duration: 700 }}
        {src}
        width="512px"
        height="340px"
        alt={`You can find this image on URL: ${src}`}
      />
    {:else}
      <div class="placeholder" />
    {/if}
  </div>
{/each}
