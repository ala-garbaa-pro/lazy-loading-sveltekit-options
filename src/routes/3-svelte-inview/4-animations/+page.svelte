<script lang="ts">
  import { inview } from "svelte-inview";
  import type { ObserverEventDetails, Options } from "svelte-inview";

  let isInView: boolean;
  let scrollDirection: Direction;
  const options: Options = {
    rootMargin: "-50px",
    unobserveOnEnter: true,
  };

  const handleChange = ({ detail }: CustomEvent<ObserverEventDetails>) => {
    console.log("detail.inView =>", detail.inView);
    
    isInView = detail.inView;
    if (detail.scrollDirection.vertical) {
      scrollDirection = detail.scrollDirection.vertical;
    }
  };
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

<div style="height: 1200px; width:50px"></div>

<div style="background-color: #165665; width: 500px, height: 600px" use:inview={options} on:inview_change={handleChange}>
  <div
    class:animate={isInView}
    class:animateFromBottom={scrollDirection === "down"}
    class:animateFromTop={scrollDirection === "up"}
  >
    Animate me! {console.log(isInView)}
  </div>
</div>

<style>
  .animate {
    transition: all 0.3s ease;
  }

  .animateFromBottom {
    transition: transform 0.3s ease;
  }

  .animateFromTop {
    transition: transform 0.3s ease;
  }

  .animateFromBottom {
    transform: translateY(100px);
  }

  .animateFromBottom.isInView {
    transform: translateY(0%);
  }

  .animateFromTop {
    transform: translateY(-100px);
  }

  .animateFromTop.isInView {
    transform: translateY(0%);
  }
</style>
