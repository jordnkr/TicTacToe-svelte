<script>
  import { createEventDispatcher } from "svelte";
  import Square from "./Square.svelte";
  export let squares;

  const dispatch = createEventDispatcher();

  function move(i) {
    dispatch("move", i);
  }
</script>

<div class="board">
  <div class="board-row">
    <Square value={squares[0]} on:click={() => move(0)} />
    <Square value={squares[1]} on:click={() => move(1)} />
    <Square value={squares[2]} on:click={() => move(2)} />
  </div>
  <div class="board-row">
    <Square value={squares[3]} on:click={() => move(3)} />
    <Square value={squares[4]} on:click={() => move(4)} />
    <Square value={squares[5]} on:click={() => move(5)} />
  </div>
  <div class="board-row">
    <Square value={squares[6]} on:click={() => move(6)} />
    <Square value={squares[7]} on:click={() => move(7)} />
    <Square value={squares[8]} on:click={() => move(8)} />
  </div>
</div>

<style>
  .board {
    margin-left: auto;
    margin-right: auto;
    display: table;
  }

  .board-row {
    margin: 0 auto;
  }

  @media screen and (max-width: 175px) {
    .board {
      margin-top: 25px;
    }

    .board-row {
      margin-top: -5px;
    }
  }
</style>
