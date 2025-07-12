<script setup lang="ts">
import { ref } from 'vue'
import PixForm from './PixForm.vue'
import CreditForm from './CreditForm.vue'

const formaSelecionada = ref<'pix' | 'credito' | null>(null)
const email = ref('')

function selecionarForma(forma: 'pix' | 'credito') {
  formaSelecionada.value = forma
}

</script>

<template>
<div class="form-container">
  <h2>CAMPEONATO DE LUTA PAULISTA</h2>
  <br>
    <form>
      <div class="form-group">
        <label for="nome">NOME COMPLETO</label>
        <input type="text" id="nome" name="nome" placeholder="Digite seu nome completo" required>
      </div>

      <div class="form-group">
        <div id="multiple-lables" style="display: flex;">
          <label for="nascimento" style="width: 40%; text-align: left; margin-right: 15%;">NASCIMENTO</label>
          <label for="sexo" style="width: 40%; text-align: left;">SEXO</label>
        </div>

        <div style="display: flex; ">
          <input type="date" id="nascimento" name="nascimento" style="width: 50%; display: flex; margin-right: 5%;" required>

          <select id="sexo" name="sexo" style="width: 50%; display: flex;" required>
            <option value="" disabled selected>Selecione</option>
            <option value="masculino">Masculino</option>
            <option value="feminino">Feminino</option>
          </select>
        </div>
      </div>

      <div class="form-group">

      </div>

      <div class="form-group">
        <div style="display: flex;">
          <label for="altura" style="width: 50%;">ALTURA EM METROS</label>
          <label for="cpf" style="width: 50%;">CPF</label>
        </div>

        <div style="display: flex;">
          <input type="text" id="altura" name="altura" placeholder="Ex: 1,75" style="width: 50%; margin-right: 5%;" required>
          <input type="text" id="cpf" name="cpf" placeholder="000.000.000-00" style="width: 50%" required>
        </div>

      </div>

      <div class="form-group">
        <label for="email" style="display:flex; width: 100%; text-align: left;">E-MAIL</label>
        <input
          type="email"
          id="email"
          name="email"
          v-model="email"
          placeholder="exemplo@email.com"
          required
        />      
      </div>

      <div class="form-group" style="display: block;">
        <label for="celular" style="display:flex; width: 100%; text-align: left;">CELULAR</label>
        <input type="tel" id="celular" name="celular" placeholder="(11) 91234-5678" required>
      </div>

      <div >
        <h2>FORMA DE PAGAMENTO</h2>
        <div style="display: flex; margin: 25px; gap: 10px;">
          <button
            type="button"
            :style="{ backgroundColor: formaSelecionada === 'pix' ? '#4CAF50' : 'grey' }"
            @click="selecionarForma('pix')"
          >
            PIX
          </button>
          <button
            type="button"
            :style="{ backgroundColor: formaSelecionada === 'credito' ? '#4CAF50' : 'grey' }"
            @click="selecionarForma('credito')"
          >
            CRÉDITO
          </button>
       </div>

        <!-- Aqui renderiza o componente conforme a escolha -->
        <div>
          <PixForm v-if="formaSelecionada === 'pix'" :email="email" />
          <CreditForm v-if="formaSelecionada === 'credito'" />
        </div>
      </div>

    </form>
  </div>
</template>

<style >
@import url('https://fonts.googleapis.com/css2?family=Ubuntu&display=swap');

    body {
      background-color: #1e1e1e;
      font-family: 'Ubuntu', sans-serif;
      color: white;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      margin: 0;
    }

    .form-container {
      background-color: #2c2c2c;
      padding: 50px;
      border-radius: 8px;
      width: 100%;
      max-width: 400px;
      box-shadow: 0 0 10px rgba(0,0,0,0.5);
    }

    .form-group {
      margin-bottom: 20px;
      display: block;
      width: 100%;
    }

    label {
      margin-bottom: 6px;
      font-size: 16px;
      text-align: left;
    }

    input, select {
      width: 100%;
      padding: 10px;
      border: 1px solid #888;
      border-radius: 4px;
      background-color: #3a3a3a;
      color: white;
      font-size: 14px;
      outline: none;
    }

    input::placeholder {
      color: #ccc;
    }

    button {
      width: 100%;
      padding: 12px;
      border: none;
      border-radius: 4px;
      background-color: #4CAF50;
      color: white;
      font-size: 16px;
      cursor: pointer;
      transition: background 0.3s ease;
    }

    button:hover {
      background-color: #45a049;
    }

</style>
