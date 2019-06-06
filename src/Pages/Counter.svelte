<script>
  import { counter } from "../Store/store.js";
  import Button from "../Components/Button.svelte";

  const increment = () => {
    counter.update(val => val + 1);
  };

  const decrement = () => counter.update(val => val - 1);
</script>

<Button title="+" on:click={increment} />
<Button title="-" on:click={decrement} />
