<script setup>
import { reactive, ref } from "vue";
const nome = ref("");
const idade = ref(null);
const email = ref("");
const senha = ref("");
const confirmarSenha = ref("");
const endereco = ref("");
const cidade = ref("");
const hobbie = ref("");
const linguagens = ref("");
const biografia = ref("");
const mostrarMensagem = ref(false);
const estados = reactive([
  "AC",
  "AL",
  "AP",
  "AM",
  "BA",
  "CE",
  "DF",
  "ES",
  "GO",
  "MA",
  "MT",
  "MS",
  "MG",
  "PA",
  "PB",
  "PR",
  "PE",
  "PI",
  "RJ",
  "RN",
  "RS",
  "RO",
  "RR",
  "SC",
  "SP",
  "SE",
  "TO",
]);
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
  if (senha.value != confirmarSenha) {
    alert("As senhas não conferem.");
    return false;
  }
  if (endereco.value === "") {
    alert("O endereço é obrigatório.");
    return false;
  }
  if (cidade.value === "") {
    alert("A cidade é obrigatório.");
    return false;
  }
  if (!estados.value) {
    alert("Selecione um estado.");
    return false;
  }
  if (hobbie === "") {
    alert("Adicione algum hobbie.")
    return false;
  }
  if (linguagens === "") {
    alert("Linguagem preferida é obrigatória.");
    return false;
  }
  if (biografia === "") {
    alert("Biografia é obrigatória.")
    return false;
  }
  return true;
}
</script>
<template>
  <div class="form">
    <div class="forms">
      <form action="">
        <legend><h2>Dados pessoais</h2></legend>
        <label for="nome">Nome:</label>
        <input type="text" id="nome" v-model.lazy="nome" />
        <label for="idade">Data de nascimento:</label>
        <input type="date" id="idade" v-model.number.lazy="idade" />
        <label for="email">E-mail:</label>
        <input type="email" id="email" v-model.lazy="email" />
        <label for="password">Senha:</label>
        <input type="password" id="password" v-model.lazy="password" />
        <label for="password">Confirmar Senha:</label>
        <input
          type="password"
          id="confirmarSenha"
          v-model.lazy="confirmarSenha"
        />
        <button @click="enviarFormulario">Enviar</button>
      </form>
    </div>
    <div class="forms">
      <form action="">
        <legend><h2>Dados pessoais</h2></legend>
        <label for="endereco">Endereço</label>
        <input type="text" id="endereco" v-model.lazy="endereco" />
        <label for="cidade">Cidade</label>
        <input type="text" id="cidade" v-model.lazy="cidade" />
        <label for="estados">Estado</label>
        <select name="estados" id="estados">
          <option value="" v-for="(item, index) in estados" :key="index">
            {{ item }}
          </option>
        </select>
        <button @click="enviarFormulario">Enviar</button>
      </form>
    </div>
    <div class="forms">
      <form action="">
        <legend><h2>Diversos</h2></legend>
        <label for="hobbies">Hobbies</label>
        <input type="text" id="hobbie" v-model.lazy="hobbie" />
        <label for="cidade">Linguagens de Programação</label>
        <input type="text" id="linguagens" v-model.lazy="linguagens" />
        <label for="biografia">Biografia</label>
        <textarea id="biografia" name="story" rows="5" cols="33"></textarea>
        <button @click="enviarFormulario">Enviar</button>
      </form>
    </div>
  </div>
  <div class="resultado" v-if="mostrarMensagem">
    <p v-if="mostrarMensagem">Dados enviados com sucesso:</p>
    <ul v-if="mostrarMensagem">
      <li>Nome: {{ nome }}</li>
      <li>Idade: {{ idade }}</li>
      <li>E-mail: {{ email }}</li>
    </ul>
  </div>
</template>
<style scoped>
@import "./sass/style.css";
</style>