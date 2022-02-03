<script lang="ts">
  import { createEventDispatcher } from "svelte";
  import { fade } from "svelte/transition";
  import { center, top, right, bottom, left } from "./animation";
  interface animationType {
    center: Function;
    top: Function;
    right: Function;
    bottom: Function;
    left: Function;
  }
  const dispatch = createEventDispatcher();
  function handleChange() {
    dispatch("change", false);
  }
  const animationFun: animationType = {
    center,
    top,
    right,
    bottom,
    left,
  };
  export let show;
  export let position: keyof animationType = "center";
  export let duration = 300;
  export let delay = 0;
  $: animationPosition = animationFun[position];
</script>

<div class="ab-pop-up">
  {#if show}
    <div
      class="night layer"
      transition:fade={{ duration, delay }}
      on:click={handleChange}
      on:touchmove|preventDefault
    />
    <div
      transition:animationPosition={{ duration, delay }}
      class="layer {position}"
    >
      <slot />
    </div>
  {/if}
</div>

<style>
  .layer {
    position: fixed;
    z-index: 10;
  }
  .yxl-pop-up {
    position: absolute;
    top: 0;
  }
  .night {
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.8);
  }
  .center {
    transform: translate(-50%, -50%);
    top: 50%;
    left: 50%;
    transform-origin: 0 0;
  }
  .top {
    top: 0;
    left: 0;
  }
  .right {
    top: 0;
    right: 0;
  }
  .bottom {
    bottom: 0;
    left: 0;
  }
  .left {
    top: 0;
    left: 0;
  }
</style>
