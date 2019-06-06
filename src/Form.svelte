<script>
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

  #cep {
    width: 180px;
  }

  .button_cep {
    margin-right: 26px;
    border: none;
    border-radius: 2px;
    color: #fff;
    background-color: #000;
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
    <div class="input">
      <label for="name">Nome:</label>
      <input id="name" bind:value={form.name} type="text" />
    </div>
    <div class="input">
      <label for="email">Email:</label>
      <input id="email" bind:value={form.email} type="text" />
    </div>
    <div class="cep">
      <div class="input">
        <label for="cep">CEP:</label>
        <input id="cep" bind:value={form.address.cep} type="text" />
      </div>
      <div>
        <button type="button" class="button_cep" on:click={searchCep}>
          Buscar
        </button>
      </div>
    </div>
    <div class="input">
      <label for="street">Rua:</label>
      <input id="street" bind:value={form.address.street} type="text" />
    </div>
    <div class="input">
      <label for="number">Número:</label>
      <input id="number" bind:value={form.address.number} type="text" />
    </div>
    <div class="input">
      <label for="city">Cidade:</label>
      <input id="city" bind:value={form.address.city} type="text" />
    </div>
  </section>
</form>
