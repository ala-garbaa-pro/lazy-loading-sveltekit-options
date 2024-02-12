<script lang="ts">
  import { inview } from "svelte-inview";
  let videoRef: HTMLVideoElement;
</script>

<h1>Video Control</h1>

<p>
  You can play/pause a video when it's in/out of the viewport. Simply pass
  correct methods in on:inview_enter and on:inview_leave callbacks.
</p>
<hr />

<div style="height: 900px; width:50px"></div>
<div
  use:inview
  on:inview_enter={() => videoRef.play()}
  on:inview_leave={() => videoRef.pause()}
>
  <video width="500" controls bind:this={videoRef} poster="/poster.png">
    <source src="/test.mp4" type="video/mp4" />
    <track kind="captions" />
  </video>
</div>
