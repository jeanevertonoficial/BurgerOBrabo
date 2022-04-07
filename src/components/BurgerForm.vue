<template>
  <div>
    <p>Componente de mensagem</p>
    <form id="burger-form">
      <div class="input-container">
        <label for="nome">Nome do cliente:</label>
        <input type="text" id="nome" v-model="nome" placeholder="Digite o seu nome">
      </div>
      <div class="input-container">
        <label for="pao">Escolhe o pão:</label>
        <select name="pao" id="pao" v-model="pao">
          <option value="" selected>Selecione o seu pão</option>
          <option v-for="pao in paes" :key="pao.id" :value="pao.tipo">
            {{pao.tipo}}
          </option>
        </select>
      </div>
      <div id="opcionais-container" class="input-container">
        <label id="opcionais-title" for="opcionais">Escolhe a carne:</label>
        <div class="check-container">
          <input type="checkbox" value="salame" id="opcionais" v-model="opcionais">
          <span>Salame</span>
        </div>
      </div>
      <div class="input-container">
        <input type="submit" class="submit-btn" value="Criar meu Burger">
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: "BurgerForm",
  data() {
    return {
      // dados que vem do servidor
      paes: null,
      carnes: null,
      opcionaisdata: null,
      //dados que vai ser inserido ao servidor
      nome: null,
      pao: null,
      carne: null,
      opcionais: [],
      status: "Solicitado",
      msg: null
    }
  },
  //medotos para trazer os dados do servidor
  methods: {
    async getIngredientes() {

      //fazendo a requisição do banco "API"
      const req = await fetch("http://localhost:3000/ingredientes");
      // fazendo a leitura da requisição em json array
      const data = await req.json();

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisdata = data.opcionaisdata;
      }
  },
  mounted() {
    //fazendo a chamado
    this.getIngredientes();
  }
}
</script>

<style scoped>
#burger-form {
  max-width: 400px;
  margin: 0 auto;
}

.input-container {
  display: flex;
  flex-direction: column;
  margin-bottom: 20px;
}

label {
  font-weight: bold;
  margin-bottom: 15px;
  color: #222222;
  padding: 5px 10px;
  border-left: 4px solid #ff9d00
}

input, select {
  padding: 5px 10px;
  width: 300px
}

#opcionais-container {
  flex-direction: row;
  flex-wrap: wrap
}

#opcionais-title {
  width: 100%;
}

.check-container {
  display: flex;
  align-items: flex-start;
  width: 50%;
  margin-bottom: 20px;
}

.check-container span, .check-container input {
  width: auto;
}

.check-container span {
  margin-left: 6px;
  font-weight: bold;
}

.submit-btn {
  background: #222222;
  color: #e58d04;
  font-weight: bold;
  border: 2px solid #222222;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.submit-btn:hover {
  transition: 0.5s;
  background: #e58d04;
  color: #222222;
}
</style>