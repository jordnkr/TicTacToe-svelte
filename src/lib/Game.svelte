<script>
  import Board from "./Board.svelte";
  import CurrentPlayer from "./CurrentPlayer.svelte";
  import Results from "./Results.svelte";

  let player = "X";
  let winner = null;
  let turn = 0;
  let squares = Array(9);

  function calculateWinner() {
    const lines = [
      [0, 1, 2],
      [3, 4, 5],
      [6, 7, 8],
      [0, 3, 6],
      [1, 4, 7],
      [2, 5, 8],
      [0, 4, 8],
      [2, 4, 6],
    ];
    for (let i = 0; i < lines.length; i++) {
      const [a, b, c] = lines[i];
      if (
        squares[a] &&
        squares[a] === squares[b] &&
        squares[a] === squares[c]
      ) {
        winner = squares[a];
      }
    }
  }

  function move(event) {
    const i = event.detail;
    if (!squares[i] && !winner) {
      turn += 1;
      squares[i] = player;

      calculateWinner();

      if (!winner) {
        player === "X" ? (player = "O") : (player = "X");
      }
    }
  }

  function reset() {
    player = "X";
    winner = null;
    turn = 0;
    squares = Array(9);
  }
</script>

<div class="game">
  <h1>Tic Tac Toe</h1>
  <CurrentPlayer {player} />
  <Board on:move={move} {squares} />
  <div class="results-section">
    {#if winner}
      <Results message={`Winner is ${winner}!`} on:reset={reset} />
      <p>{turn}</p>
    {/if}
    {#if !winner && turn >= 9}
      <Results message="The game is a draw!" on:reset={reset} />
    {/if}
  </div>
</div>

<style>
  h1 {
    margin-top: 0;
    padding-top: 0px;
  }

  .game {
    text-align: center;
    margin: 0;
    position: absolute;
    top: 40%;
    left: 50%;
    -ms-transform: translate(-50%, -50%);
    transform: translate(-50%, -50%);
  }

  .results-section {
    position: fixed;
    left: 0;
    right: 0;
    text-align: center;
  }
</style>
