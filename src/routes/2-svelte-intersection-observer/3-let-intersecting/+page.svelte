<script lang="ts">
  import IntersectionObserver from "svelte-intersection-observer";
  import { fade } from "svelte/transition";

  let node: HTMLElement;
</script>

<h1>let:intersecting</h1>
<p>
  An alternative to binding to the intersecting prop is to use the let:
  directive.
</p>
<p>
  In the following example, the "Hello world" element will fade in when its
  containing element intersects the viewport.
</p>
<div
  style="margin-top: 69px; width: 100%; height: 200vh; background-color: goldenrod; opacity:0.5"
>
  ..
</div>

<IntersectionObserver element={node} let:intersecting>
  <div bind:this={node}>
    {#if intersecting}
      <div
        style="color: chocolate; font-weight: 900; padding: 20px; font-size: 5rem;"
        transition:fade={{ delay: 200 }}
      >
        Hello world
      </div>
    {/if}
  </div>
</IntersectionObserver>

<div style="width: 1px; height: 200vh;">..</div>
