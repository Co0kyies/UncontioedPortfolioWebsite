<script>
  let dark = false;
  let localTheme = localStorage.getItem("dark");
  if (localTheme) {
    if (localTheme === "true") {
      dark = true;
    } else {
      dark = false;
    }
  }
</script>

<svelte:head>
  <script
    src="https://kit.fontawesome.com/25cce9fa61.js"
    crossorigin="anonymous"></script>
</svelte:head>

<main class:dark>
  <button
    class:dark
    on:click={() => {
      dark = !dark;
      localStorage.setItem("dark", dark);
    }}
    >{#if dark}
      <i class="fa-solid fa-sun" />
    {:else}
      <i class="fa-solid fa-moon" />
    {/if}
  </button>
  <slot />
</main>

<style lang="scss">
  button {
    position: fixed;
    left: 1.8rem;
    bottom: 1.8rem;
    background-color: transparent;
    border: none;
    font-size: 2rem;
    &.dark {
      color: white;
    }
  }
</style>
