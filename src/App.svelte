<script lang="ts">
  import { onMount } from "svelte";
  import { writable } from "svelte/store";
  import "papercss";
  import Counter from "./Counter.svelte";
  import Link from "./components/Link.svelte";

  const count = writable(100);

  export let name: string;
  onMount(() => {
    console.log("App mounted");
  });
</script>

<div class="text-center">
  <h1>Hello {name}!</h1>
  <Link url="/"><h2>home</h2></Link>
  <p>
    <Counter />
    <Counter value={1}>Counter 1</Counter>
    <Counter value={$count} step={3}>Counter 2</Counter>
  </p>
</div>

<style>
  h1 {
    color: purple;
  }
</style>
