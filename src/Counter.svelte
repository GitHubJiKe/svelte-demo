<script lang="ts">
  import { beforeUpdate, afterUpdate } from "svelte";
  import Button from "./components/Button.svelte";

  export let value: number = 0;
  export let step: number = 1;
  beforeUpdate(() => {
    console.log(value);
  });

  afterUpdate(() => {
    console.log(step);
  });
</script>

<div>
  <slot>Default Counter</slot>
  <div>
    {value}
    <Button
      size="large"
      color="success"
      type="link"
      onClick={() => {
        value += step;
      }}>+</Button
    >
    <Button
      onClick={() => {
        value -= step;
      }}>-</Button
    >
  </div>
</div>
