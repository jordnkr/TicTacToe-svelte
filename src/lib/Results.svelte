<script>
  import { createEventDispatcher } from "svelte";

  const dispatch = createEventDispatcher();

  function reset() {
    dispatch("reset");
  }
</script>

<p><slot /></p>
<button on:click={reset}>Play Again</button>
