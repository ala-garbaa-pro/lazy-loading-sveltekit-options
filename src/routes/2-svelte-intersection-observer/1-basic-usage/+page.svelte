<script lang="ts">
  import IntersectionObserver from "svelte-intersection-observer";

  let element: HTMLElement;
  let intersecting: boolean;
</script>

<header
  class:intersecting
  style="width: 100%; height: 64px; background-color: tomato; position: fixed; top: 0; left: 0; z-index: 1000  opacity:0.9"
>
  {intersecting ? "Element is in view" : "Element is not in view"}
</header>

<h1>Basic</h1>
<p>
  Use the bind:this directive to pass an element reference to the
  IntersectionObserver component.
</p>

<p>
  Then, simply bind to the reactive intersecting prop to determine if the
  element intersects the viewport.
</p>

<div
  style="margin-top: 69px; width: 100%; height: 200vh; background-color: goldenrod; opacity:0.5"
>
  ..
</div>
<IntersectionObserver {element} bind:intersecting>
  <div bind:this={element}>Hello world</div>
</IntersectionObserver>

<div style="width: 1px; height: 200vh;">..</div>
