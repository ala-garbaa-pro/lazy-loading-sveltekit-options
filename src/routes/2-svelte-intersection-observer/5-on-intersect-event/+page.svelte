<script lang="ts">
  import IntersectionObserver from "svelte-intersection-observer";

  let element: HTMLElement;
</script>

<h1>on:intersect event</h1>
<p>
  As an alternative to binding the intersecting prop, you can listen to the
  intersect event that is dispatched if the observed element is intersecting the
  viewport.
</p>

<p>
  Note: Compared to on:observe, on:intersect is dispatched only when the element
  is intersecting the viewport. In other words, e.detail.isIntersecting will
  only be true.
</p>
<div
  style="margin-top: 69px; width: 100%; height: 200vh; background-color: goldenrod; opacity:0.5"
>
  ..
</div>

<IntersectionObserver
  {element}
  on:intersect={(e) => {
    console.log(e.detail); // IntersectionObserverEntry
    console.log(e.detail.isIntersecting); // true
  }}
>
  <div bind:this={element}>Hello world</div>
</IntersectionObserver>

<div style="width: 1px; height: 200vh;">..</div>
