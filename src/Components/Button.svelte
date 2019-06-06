<script>
  export let title;
</script>

<style>
  button {
    margin-right: 26px;
    border: none;
    border-radius: 2px;
    color: #fff;
    background-color: #000;
    min-width: 50px;
  }
  button:active {
    background-color: #282828;
    box-shadow: 0px 0px 5px #282828;
  }
</style>

<button type="button" on:click>{title}</button>
