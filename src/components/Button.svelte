<script lang="ts">
  import Link from "./Link.svelte";

  export let onClick: () => void;
  export let size: "large" | "default" | "small" = "default";
  export let type: "link" | "block" | undefined = undefined;
  export let color:
    | "primary"
    | "secondary"
    | "success"
    | "warning"
    | "danger"
    | undefined = undefined;
  export let outline: boolean = false;
  export let disabled: boolean = false;
  export let url: string = "";

  let className = "",
    isLink = type === "link";

  if (type) {
    if (type === "block") {
      className += `btn-block`;
    }
    if (isLink) {
      className += `paper-btn`;
    }
  }
  if (size) {
    className += ` btn-${size}`;
  }

  if (color) {
    if (outline) {
      className += ` btn-${color}-outline`;
    } else {
      className += ` btn-${color}`;
    }
  }
</script>

{#if isLink}
  <Link
    on:click={onClick}
    {url}
    disabled={disabled ? disabled : undefined}
    {className}><slot /></Link
  >
{:else}
  <button
    on:click={onClick}
    disabled={disabled ? disabled : undefined}
    class={className}><slot /></button
  >
{/if}
