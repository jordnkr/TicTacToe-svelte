<script>
  export let player;
</script>

<div class="current-player">
  <span class="label">Current Player</span>
  <span>{player}</span>
</div>

<style>
  .current-player {
  margin-bottom: 15px;
}

.current-player > span {
  display: block;
}

.label{
  text-decoration: underline;
}
</style>