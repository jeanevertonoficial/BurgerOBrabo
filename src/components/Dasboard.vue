<template>
  <div id="burguer-table">
    <div>
      <div id="burguer-table-heading">
        <div class="order-id">#</div>
        <div>Cliente</div>
        <div>Pão</div>
        <div>Carne</div>
        <div>Opcionais</div>
        <div>Ações</div>
      </div>
      <div id="burger-table-rows"  v-for="burger in burgers" :key="burger.id">
        <div class="burger-table-row">
          <div class="order-number">{{ burger.id }}</div>
          <div>{{ burger.nome }}</div>
          <div>{{ burger.pao }}</div>
          <div>{{ burger.carne }}</div>
          <div>
            <ul>
              <li v-for="(opcional, index) in burger.opcionais" :key="index">
                {{ opcional }}
              </li>
            </ul>
          </div>
          <div>
            <select name="status" class="status" @change="updatedBurger($event, burger.id)">
              <option v-for="s in status"
                      :key="s.id"
                      :value="s.tipo"
                      :selected="burger.status == s.tipo">
              {{ s.tipo }}
              </option>
            </select>
            <button class="delete-btn" @click="deleteBurger(burger.id)">Cancelar</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Dasboard",
  data() {
    return {
      burgers: null,
      burger_id: null,
      status: []
    }
  },
  methods: {
    async getPedidos() {

      const req = await fetch("http://localhost:3000/burgers");

      const data = await req.json();

      this.burgers = data;

      console.log(this.burgers);

      this.getStatus();
    },
    async getStatus() {

      const req = await fetch("http://localhost:3000/estado");

      const data = await req.json();

      this.status = data;

    },
    async deleteBurger(id)  {

      const  req = await fetch(`http://localhost:3000/burgers/${id}`, {
        method: "DELETE"
      });

      const res = await req.json();

      // msg

      this.getPedidos();

    },
    async updatedBurger( event, id ){

      const option = event.target.value;

      const dataJson = JSON.stringify({ status: option });

      const req = await fetch(`http://localhost:3000/bugers/${id}`, {
        method: "PATCH",
        headers: { "Content-Type": "application/json"},
        body: dataJson
      });

      const res = await req.json();

      console.log(res);
    }
  },
  mounted() {
    this.getPedidos();
  }
}
</script>

<style scoped>
#burguer-table {
  max-width: 1200px;
  margin: 0 auto;
}

#burguer-table-heading,
#burger-table-rows,
.burger-table-row {
  display: flex;
  flex-direction: row;
}

#burguer-table-heading {
  font-weight: bold;
  padding: 12px;
  border-bottom: 3px solid #333;
}

#burguer-table-heading div,
.burger-table-row div {
  width: 100%;
}

.burger-table-row {
  width: 100%;
  padding: 12px;
  border-bottom: 1px solid #ccc;
}

#burguer-table-heading .order-id,
.burger-table-row .order-number {
  width: 5%;
}

select {
  padding: 12px 0px;
  margin-right: 12px;
}

.order-number, .order-id {
  margin-right: 10px;
}

.delete-btn {
  background: #222;
  color: #e58d04;
  font-weight: bold;
  border: 2px solid #222;
  border-radius: 5px;
  padding: 10px;
  font-size: 16px;
  margin: 0 auto;
  cursor: pointer;
  transition: 0.5s;
}

.delete-btn:hover {
  background: #e58d04;
  color: #222222;
}
</style>