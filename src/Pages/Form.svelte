<script>
  import Input from "../Components/Input.svelte";
  import InputNumber from "../Components/InputNumber.svelte";
  let form = {
    name: "",
    email: "",
    address: {
      cep: "",
      street: "",
      number: "",
      city: ""
    }
  };

  const searchCep = async () => {
    const request = await fetch(
      `https://viacep.com.br/ws/${form.address.cep}/json`
    );
    const cep = await request.json();
    if (cep.erro) return;

    form.address.cep = cep.cep;
    form.address.street = cep.logradouro;
    form.address.city = cep.localidade;
  };

  $: console.log(form.address.cep);
</script>

<style>
  .title {
    text-align: center;
    font-size: 2rem;
  }
  section {
    padding: 15px;
    margin: 0 auto;
    width: 80vw;
    border-radius: 2px;
    box-shadow: 5px 5px 5px rgba(0, 0, 0, 0.2);
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    background-color: #eee;
  }

  .input {
    width: 100%;
  }

  .cep {
    display: flex;
    align-items: flex-end;
    justify-content: flex-end;
  }
</style>

<h1 class="title">1st form in svelte</h1>
<form>
  <section>
    <Input label="Nome" id="name" value={form.name} />
    <Input label="Email" id="email" value={form.email} />

    <div class="cep">
      <Input label="CEP" id="cep" bind:value={form.address.cep} />
      <div>
        <button type="button" class="button_cep" on:click={searchCep}>
          Buscar
        </button>
      </div>
    </div>
    <Input label="Rua" id="street" bind:value={form.address.street} />
    <InputNumber
      label="Número"
      id="number"
      bind:value={form.address.number}
      type="text" />
    <div class="input">
      <label for="city">Cidade:</label>
      <input id="city" bind:value={form.address.city} type="text" />
    </div>
  </section>
</form>
