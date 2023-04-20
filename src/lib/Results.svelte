<script>
  import { createEventDispatcher } from "svelte";
  export let message;

  const dispatch = createEventDispatcher();

  function reset() {
    dispatch('reset');
  }
</script>

<div>
  <p>{message}</p>
  <button on:click={reset}>Play Again</button>
</div>