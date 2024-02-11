<script lang="ts">
  import IntersectionObserver from "svelte-intersection-observer";

  let element: HTMLElement;
</script>

<h1>on:observe event</h1>
<p>
  The observe event is dispatched when the element is first observed and also
  whenever an intersection event occurs.
</p>
<div
  style="margin-top: 69px; width: 100%; height: 200vh; background-color: goldenrod; opacity:0.5"
>
  ..
</div>

<IntersectionObserver
  {element}
  on:observe={(e) => {
    console.log(e.detail); // IntersectionObserverEntry
    console.log(e.detail.isIntersecting); // true | false
  }}
>
  <div bind:this={element}>Hello world</div>
</IntersectionObserver>

<div style="width: 1px; height: 200vh;">..</div>
