<script>
  import Form from "./Pages/Form.svelte";
  import Counter from "./Pages/Counter.svelte";
  import { counter } from "./Store/store";

  let counterValue;
  counter.subscribe(val => (counterValue = val));
</script>

<Form />
<Counter />
<h1>Contador: {counterValue}</h1>
