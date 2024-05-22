<script>
  import { onMount } from "svelte";
  import { tweened } from "svelte/motion";
  import { cubicOut } from "svelte/easing";
  //On mouseMove
  let translateX = tweened(0, {
    duration: 2500,
    easing: cubicOut,
  });
  let translateY = tweened(0, {
    duration: 2500,
    easing: cubicOut,
  });
  //Defining the parent div
  let div;
  function handleMousemove() {
    //Waiting for the mounting
  }
  onMount(() => {
    handleMousemove = function (event) {
      translateX.set(event.clientX - div.clientWidth / 2);
      translateY.set(event.clientY - div.clientHeight / 2);
    };
  });
</script>

<div on:mousemove={handleMousemove} bind:this={div} id="hero">
  <div
    class="text"
    style="transform: translate({$translateX / 70}px, {$translateY / 70}px);"
  >
    <span class="greetings">Здравей Аз Съм</span>

    <h1>
      <span>НИКОЛА</span>
      <span>СЛАВОВ</span>
    </h1>

    <span style="opacity: 0;">.</span>
  </div>
</div>

<style lang="scss">
  @import "../styles/breaking_points.scss";
  #hero {
    cursor: default;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 100vh;
    margin: auto;
    font-family: "Cormorant SC", serif;
    .text {
      position: relative;
      // overflow: hidden;
      h1 {
        position: relative;
        font-size: 20vw;
        line-height: 15vw;

        margin: 0;
        text-align: center;
        span {
          display: block;
        }
      }
      & .greetings {
        display: block;
        width: 100%;
        text-align: start;
        font-size: 8vw;
        @include wildscreen {
          font-size: 3.5vw;
        }
        margin: 0;
        padding: 0;
      }
    }
  }
</style>
