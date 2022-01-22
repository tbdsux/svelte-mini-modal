<script>
  // based from here https://github.com/sveltejs/svelte/issues/3088#issuecomment-505785516

  import { onDestroy,onMount } from "svelte";

  /**
   * @type {HTMLDivElement}
   */
  let ref;

  /**
   * CSS modal parent class names style.
   * @type {string}
   */
  export let className = "";

  /**
   * Modal overlay class names style.
   * @type {string}
   */
  export let overlayClassName = "";

  /**
   * Show modal.
   * @type {boolean}
   */
  export let open;

  /**
   * Function to trigger on modal close call.
   * @type {function}
   */
  export let onClose;

  onMount(() => {
    let el = document.createElement("div");

    document.body.removeChild(el);
    el.appendChild(ref);
  });

  onDestroy(() => {
    document.body.removeChild(ref);
  });
</script>

{#if open}
  <div bind:this={ref} class={className}>
    <div class={overlayClassName} on:click={onClose} />

    <slot />
  </div>
{/if}
