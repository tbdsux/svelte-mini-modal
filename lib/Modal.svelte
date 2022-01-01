<script>
  // based from here https://github.com/sveltejs/svelte/issues/3088#issuecomment-505785516

  import { onDestroy, onMount } from "svelte";

  let ref;
  export let className = "";
  export let overlayClassName = "";
  export let open;
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
