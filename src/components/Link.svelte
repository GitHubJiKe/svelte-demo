<script lang="ts">
  import { createEventDispatcher } from "svelte";
  export let url: string = "";
  export let className: string = "";
  export let disabled: boolean = false;
  export let onClick: (() => void) | undefined = undefined;

  const dispatch = createEventDispatcher();
</script>

{#if url}
  <a class={className} href={url} disabled={disabled ? disabled : undefined}
    ><slot /></a
  >
{:else}
  <a
    class={className}
    on:click={(e) => dispatch("click", e)}
    disabled={disabled ? disabled : undefined}
  >
    <slot />
  </a>
{/if}

<style>
  a {
    user-select: none;
  }
</style>
