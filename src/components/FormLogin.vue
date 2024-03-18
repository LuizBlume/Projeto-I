<script setup>
import { ref } from "vue";

const nome = ref("");
const idade = ref(null);
const email = ref("");
const senha = ref("");
const confirmarSenha = ref("");
const mostrarMensagem = ref(false);

function enviarFormulario() {
  if (validarFormulario()) {
    mostrarMensagem.value = true;
  }
}
function validarFormulario() {
  if (nome.value.length < 3 || nome.value.length > 20) {
    alert("O nome deve ter entre 3 e 20 caracteres.");
    return false;
  }

  if (!email.value.includes("@")) {
    alert("O e-mail deve ser válido.");
    return false;
  }
  if (senha.value === confirmarSenha) {
    alert("As senhas não conferem.");
    return false;
  }
  return true;
}
</script>

<template>
  <div class="form">
    <div>
      <label for="nome">Nome:</label>
      <input type="text" id="nome" v-model.lazy="nome" />
      <label for="idade">Data de nascimento:</label>
      <input type="date" id="idade" v-model.number.lazy="idade" />
      <label for="email">E-mail:</label>
      <input type="email" id="email" v-model.lazy="email" />
      <label for="password">Senha:</label>
      <input type="password" id="email" v-model.lazy="email" />
      <label for="password">Confirmar Senha:</label>
      <input type="password" id="confirmarSenha" v-model.lazy="confirmarSenha" />
      <button @click="enviarFormulario">Enviar</button>
      <p v-if="mostrarMensagem">Dados enviados com sucesso:</p>
      <ul v-if="mostrarMensagem">
        <li>Nome: {{ nome }}</li>
        <li>Idade: {{ idade }}</li>
        <li>E-mail: {{ email }}</li>
      </ul>
    </div>
    <div>
      <label for="nome">Nome:</label>
      <input type="text" id="nome" v-model.lazy="nome" />
      <label for="idade">Idade:</label>
      <input type="number" id="idade" v-model.number.lazy="idade" />
      <label for="email">E-mail:</label>
      <input type="email" id="email" v-model.lazy="email" />
      <button @click="enviarFormulario">Enviar</button>
      <p v-if="mostrarMensagem">Dados enviados com sucesso:</p>
      <ul v-if="mostrarMensagem">
        <li>Nome: {{ nome }}</li>
        <li>Idade: {{ idade }}</li>
        <li>E-mail: {{ email }}</li>
      </ul>
    </div>
  </div>
</template> 
<style scoped>
.container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 8px;
}
label {
  display: block;
  margin-bottom: 5px;
  font-weight: bold;
}
input {
  width: 100%;
  padding: 8px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
button {
  background-color: #007bff;
  color: #fff;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.success-message {
  color: green;
  font-weight: bold;
}
ul {
  list-style-type: none;
  padding: 0;
}
ul li {
  margin-bottom: 5px;
}
.hide {
  display: none;
}

.form {
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding: 40px;
}

.form > * {
  border: 1px solid rgb(187, 187, 187);
  padding: 20px;
  border-radius: 8px;
}
</style>