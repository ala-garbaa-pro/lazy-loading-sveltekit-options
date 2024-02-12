<script lang="ts">
  import { inview } from "svelte-inview";
  let videoRef: HTMLVideoElement;
</script>

<h1>Animations</h1>

<p>
  You can also add some cool animations when an element enters the viewport. To
  make sure the animation won't fire too soon you can pass a negative value to
  rootMargin. When inView is true, add an animation class to your target.
  Additionally, you can detect the scroll direction to make the animations even
  cooler!
</p>
<hr />

<div style="height: 900px; width:50px"></div>
<div use:inview on:inview_leave={() => videoRef.pause()}>
  <video width="500" controls bind:this={videoRef} poster="/poster.png">
    <source src="/test.mp4" type="video/mp4" />
    <track kind="captions" />
  </video>
</div>
