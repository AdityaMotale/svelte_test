<script>
  import { createEventDispatcher } from "svelte";

  const eventDispacher = createEventDispatcher();

  export let colors = ["#d58141", "#d7c44c", "#4fa9cc", "#3f8d27"];

  // Props

  export let palleteColor;
  export let bgColor = "#ffffff";
</script>

<section>
  {#each colors as color}
    <button
      on:click={() => {
        eventDispacher("color", { color });
        palleteColor = color;
      }}
      style:bgColor
      ><span class="visually-hidden">
        Select the color {color}
      </span></button
    >
  {/each}

  <button
    on:click={() => {
      eventDispacher("bgColor", { bgColor });
    }}
    style:bgColor
    ><span class="visually-hidden">
      Select the bg color {bgColor}
    </span></button
  >

  <svg style:color={palleteColor} viewBox="-50 -50 100 100">
    <g
      fill="currentColor"
      stroke="currentColor"
      stroke-width="0"
      stroke-linecap="round"
    >
      <path d="M -38 12 a 38 38 0 0 0 76 0 q 0 -28 -38 -62 -38 34 -38 62" />
    </g>
  </svg>
</section>

<style>
  section {
    --size: 1.75rem;
    padding: 0.25rem;
    display: flex;
    align-items: center;
    gap: 0 1rem;
  }

  section > svg {
    flex-shrink: 0;
  }

  button,
  section > svg {
    width: var(--size);
    height: var(--size);
  }

  button {
    cursor: pointer;
    border-radius: 50%;
    margin: 0;
  }

  section > svg {
    display: block;
  }
</style>
