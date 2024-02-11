<script lang="ts">
  import { inview } from "svelte-inview";

  let isInView: boolean;
  const options = {};
</script>

<h1>Basic Use Case</h1>

<p>
  This is the most basic use case for svelte-inview. Just add the action to the
  element you want to track - use:inview. You can also pass other configuration
  props. You can see if the element is visible by checking the inView or from
  the inside of the callback method - on:inview_change.
</p>
<hr />

<header
  class:intersecting={isInView}
  style="width: 100%; height: 64px; background-color: tomato; position: fixed; top: 0; left: 0; z-index: 1000  opacity:0.9"
>
  {isInView ? "Element is in view" : "Element is not in view"}
</header>

<div
  style="margin-top: 69px; width: 100%; height: 200vh; background-color: goldenrod; opacity:0.2"
>
  ..
</div>
<div
  use:inview={options}
  on:inview_change={(event) => {
    const { inView, entry, scrollDirection, observer, node } = event.detail;
    console.log(":: Inside inview_change");
    console.log("- inView =>", inView);
    console.log("- entry =>", entry);
    console.log("- scrollDirection =>", scrollDirection);
    console.log("- observer =>", observer);
    console.log("- node =>", node);

    isInView = inView;
  }}
  on:inview_enter={(event) => {
    const { inView, entry, scrollDirection, observer, node } = event.detail;
    isInView = inView;
  }}
  on:inview_leave={(event) => {
    const { inView, entry, scrollDirection, observer, node } = event.detail;
    isInView = inView;
  }}
  on:inview_init={(event) => {
    const { observer, node } = event.detail;
  }}
>
  {isInView ? "Hey I am in the viewport" : "Bye, Bye"}
</div>

<div
  style="margin-top: 69px; width: 100%; height: 200vh; background-color: lime; opacity:0.2"
>
  ..
</div>
