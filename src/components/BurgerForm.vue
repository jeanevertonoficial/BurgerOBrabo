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
          <option value="">Selecione o seu pão</option>
          <option value="integral">Integral</option>
        </select>
      </div>
      <div id="opcionais-container" class="input-container">
        <label id="opcionais-title" for="opcionais">Escolhe a carne:</label>
        <div class="check-container">
          <input type="checkbox" value="salame" id="opcionais" v-model="opcionais">
          <span>Salame</span>
        </div>
        <div class="check-container">
          <input type="checkbox" value="salame" id="opcionais" v-model="opcionais">
          <span>Salame</span>
        </div>
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
  name: "BurgerForm"
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