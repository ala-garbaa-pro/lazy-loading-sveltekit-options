<script lang="ts">
  import IntersectionObserver from "svelte-intersection-observer";

  let elementOnce: HTMLElement;
  let intersectOnce: boolean;
</script>

<header
  class:intersecting={intersectOnce}
  style="width: 100%; height: 64px; background-color: tomato; position: fixed; top: 0; left: 0; z-index: 1000  opacity:0.9"
>
  {intersectOnce ? "Element is in view" : "Element is not in view"}
</header>

<h1>Once</h1>
<p>
  Set once to true for the intersection event to occur only once. The element
  will be unobserved after the first intersection event occurs.
</p>
<div
  style="margin-top: 69px; width: 100%; height: 200vh; background-color: goldenrod; opacity:0.5"
>
  ..
</div>
<IntersectionObserver
  once
  element={elementOnce}
  bind:intersecting={intersectOnce}
>
  <div bind:this={elementOnce}>Hello world</div>
</IntersectionObserver>

<div style="width: 1px; height: 200vh;">..</div>
