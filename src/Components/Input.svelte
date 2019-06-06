<script>
  export let label = "";
  export let id = "";
  export let value = "";
</script>

<div>
  <label for={id}>{label}</label>
  <input {id} bind:value />
</div>
