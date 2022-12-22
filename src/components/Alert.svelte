<script lang="ts">
  import { beforeUpdate, onMount } from "svelte";
  import { CommonWarningTypes } from "../types";

  export let type: CommonWarningTypes = "primary";
  export let closable: boolean = true;
  export let defaultContent: string = "默认文案";
  let className = `alert`;
  let show: boolean = true;
  const setTypeOfClass = () => {
    className += ` alert-${type}`;
  };

  setTypeOfClass();

  onMount(() => {
    show = true;
  });

  beforeUpdate(setTypeOfClass);

  if (closable) {
    className += ` dismissible`;
  }

  const closeEvent = () => {
    let timer = setTimeout(() => {
      show = false;
      clearTimeout(timer);
      timer = null as unknown as number;
    }, 300);
  };
</script>

{#if show}
  <input class="alert-state" id="alert-1" type="checkbox" />
  <div class={className}>
    <slot>
      {defaultContent}
    </slot>
    {#if closable}
      <label class="btn-close" for="alert-1" on:click={closeEvent}>X</label>
    {/if}
  </div>
{/if}
