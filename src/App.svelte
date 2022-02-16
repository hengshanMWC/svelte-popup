<script lang="ts">
  import Popup from "./components/Popup/index.svelte";
  let showCenter = false;
  let showTop = false;
  let showRight = false;
  let showBottom = false;
  let showLeft = false;
  function toggleCenter() {
    showCenter = !showCenter;
  }
  function toggleTop() {
    showTop = !showTop;
  }
  function toggleRight() {
    showRight = !showRight;
  }
  function toggleBottom() {
    showBottom = !showBottom;
  }
  function toggleLeft() {
    showLeft = !showLeft;
  }
</script>

<main>
  <button on:click={toggleCenter}>center:{showCenter ? "hide" : "show"}</button>
  <button on:click={toggleTop}>top:{showTop ? "hide" : "show"}</button>
  <button on:click={toggleRight}>right:{showRight ? "hide" : "show"}</button>
  <button on:click={toggleBottom}>bottom:{showBottom ? "hide" : "show"}</button>
  <button on:click={toggleLeft}>left:{showLeft ? "hide" : "show"}</button>
  <Popup show={showCenter} on:change={toggleCenter}>
    <div class="center box">center</div>
  </Popup>
  <Popup show={showTop} on:change={toggleTop} position="top">
    <div class="top box ybox">top</div>
  </Popup>
  <Popup show={showRight} on:change={toggleRight} position="right">
    <div class="right box xbox">right</div>
  </Popup>
  <Popup show={showBottom} on:change={toggleBottom} position="bottom">
    <div class="bottom box ybox">bottom</div>
  </Popup>
  <Popup show={showLeft} on:change={toggleLeft} position="left">
    <div class="left box xbox">left</div>
  </Popup>
</main>

<style>
  button {
    display: block;
    margin-bottom: 15px;
  }
  .box {
    display: flex;
    align-items: center;
    justify-content: center;
    background: #fff;
  }
  .ybox {
    height: 60vh;
    width: 100vw;
  }
  .xbox {
    height: 100vh;
    width: 80vw;
  }
  .center {
    width: 50vh;
    height: 50vw;
    border-radius: 15px;
  }
  .top {
    border-radius: 0 0 15px 15px;
  }
  .right {
    border-radius: 15px 0 0 15px;
  }
  .bottom {
    border-radius: 15px 15px 0 0;
  }
  .left {
    border-radius: 0 15px 15px 0;
  }
</style>
