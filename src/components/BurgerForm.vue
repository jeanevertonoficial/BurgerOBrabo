<template>
  <div>
    <Messege :msg="msg" v-show="msg"/>
    <form id="burger-form" @submit="createBurger">
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
      <div class="input-container">
        <label for="pao">Escolhe a carne do seu Burger:</label>
        <select name="carne" id="carne" v-model="carne">
          <option value="" selected>Selecione a carne para seu burger</option>
          <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">
            {{carne.tipo}}
          </option>
        </select>
      </div>
      <div id="opcionais-container" class="input-container">
        <label id="opcionais-title" for="opcionais">Escolhe os opcionais:</label>
        <div class="check-container" v-for="opcional in opcionaisdata"
             :key="opcional.id">
          <input type="checkbox" name="opcionais" v-model="opcionais" :value="opcional.tipo"  id="opcionais" >
          <span>{{ opcional.tipo }}</span>
        </div>
      </div>
      <div class="input-container">
        <input type="submit" class="submit-btn" value="Criar meu Burger">
      </div>
    </form>
  </div>
</template>

<script>

import Messege from "@/components/Messege";

export default {
  name: "BurgerForm",
  components: {Messege},

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
      opcionais:[],
      msg: null
    }
  },
  //medotos para trazer os dados do servidor e enviar dados
  methods: {
    async getIngredientes() {

      //fazendo a requisição do banco "API"
      const req = await fetch("http://localhost:3000/ingredientes");


      // fazendo a leitura da requisição em json array
      const data = await req.json();
    //  console.log(data);

      this.paes = data.paes;
      this.carnes = data.carnes;
      this.opcionaisdata = data.opcionais;
      },
    // função para inserir os pedidos no sistemas
    async createBurger(e) {

      //ao clicar no botão do formulario pausar a execução e pegar as informações
      e.preventDefault();

     // console.log('Cadastrar com sucesso');

      // dados que vão ser inseridos no servidor

      const data = {
        nome: this.nome,
        carne: this.carne,
        pao: this.pao,
        //criando objeto array para pegar os opcionais do chekbox
        opcionais: Array.from(this.opcionais),
        status: "Solicitado",

      }
      //console.log(data);

      //formatando os dados em strings com json
      const dataJon = JSON.stringify(data);

      const req = await fetch("http://localhost:3000/burgers", {
        method: "POST",
        headers: {"content-Type": "application/json"},
        body:dataJon
      });

      //fazendo a requisição no banco
      const rest = await req.json();

      console.log("Burger O Brabo Agradece seu pedido, muito Obrigado!!");

      // Mensagem pedido realizado com sucesso
      this.msg = `Pedido N° ${rest.id} realizado com sucesso!`

      //apagando a mensagem de inserido com sucesso após 3 segundos
      setTimeout(() => this.msg = "", 3000)

      // limpa os campos após insersão
      this.nome = "";
      this.carne = "";
      this.pao = "";
      this.opcionais = "";

    }
  },
  mounted() {
    //fazendo a chamado do metodo Ingredientes
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