<script>
  export let value;
</script>

<button class="square" on:click>
  {value ? value : ""}
</button>

<style>
  .square {
    background: #fff;
    border: 1px solid #999;
    font-size: 24px;
    font-weight: bold;
    height: 50px;
    margin-right: -1px;
    margin-top: -5px;
    padding: 0;
    text-align: center;
    width: 50px;
    vertical-align: top;
  }

  .square:focus {
    outline: none;
  }

  .square:focus {
    background: #ddd;
  }

  @media (min-width: 768px) {
    .square {
      font-size: 32px;
      height: 75px;
      width: 75px;
    }
  }

  @media (max-width: 300px) {
    .square {
      font-size: 18px;
      height: 30px;
      width: 30px;
    }
  }

  @media (max-width: 175px) {
    .square {
      font-size: 12px;
      height: 15px;
      width: 15px;
    }
  }
</style>
