<script setup>
import { reactive, ref } from "vue";
const elementForms = reactive({
  nome: "",
  idade: "",
  email: "",
  senha: "",
  confirmarSenha: "",
  endereco: "",
  cidade: "",
  estados: ["AC", "AL", "AP", "AM", "BA", "CE", "DF", "ES", "GO", "MA", "MT", "MS", "MG", "PA", "PB", "PR", "PE", "PI", "RJ", "RN", "RS", "RO", "RR", "SC", "SP", "SE", "TO"],
  hobbie: "",
  linguagens: "",
  biografia: "",
  mostrarMensagem: false,
});
</script>
<template>
  <div class="form">
    <div class="forms">
      <form action="">
        <legend><h2>Dados pessoais</h2></legend>
        <label for="nome">Nome:</label>
        <input type="text" id="nome" v-model.lazy="nome" />
        <label for="data_nasc">Data de nascimento:</label>
        <input type="date" id="data_nasc" v-model.number.lazy="idade" />
        <label for="email">E-mail:</label>
        <input type="email" id="email" v-model.lazy="email" />
        <label for="password">Senha:</label>
        <input type="password" id="password" v-model.lazy="senha" />
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
  <div class="resultados-area">
    <div class="resultados-content">
      <button @click="enviarFormulario">Show informations</button>
      <div class="resultado" v-if="mostrarMensagem">
        <ul>
          <li>
            Nome: <span>{{ nome }}</span>
          </li>
          <li>
            Idade: <span>{{ idade }}</span>
          </li>
          <li>
            E-mail: <span>{{ email }}</span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>
<style scoped>
@import "./sass/style.css";
</style>