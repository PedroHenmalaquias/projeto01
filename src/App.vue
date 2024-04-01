<script setup>
import { ref, reactive, computed } from 'vue'

const user = reactive({
  nome: '',
  email: '',
  senha: '',
  confirmarSenha: '',
  dataNascimento: '',
  endereco: '',
  cidade: '',
  estado: [
    'AC',
    'AL',
    'AP',
    'AM',
    'BA',
    'CE',
    'DF',
    'ES',
    'GO',
    'MA',
    'MT',
    'MS',
    'MG',
    'PA',
    'PB',
    'PR',
    'PE',
    'PI',
    'RJ',
    'RN',
    'RS',
    'RO',
    'RR',
    'SC',
    'SP',
    'SE',
    'TO'
  ]
})
let envia = ref(false)
</script>

<template>
  <div class="container">
    <h1>Insira seus dados de usuário</h1>
    <form action="" @submit.prevent>
      <div class="itens">
        <input type="text" name="" id="" placeholder="Nome" v-model="user.nome" />
      </div>
      <div class="itens">
        <input type="email" name="" id="" placeholder="Email" v-model="user.email" />
      </div>
      <div class="itens">
        <input type="password" name="" id="" placeholder="Senha" v-model="user.senha" />
      </div>
      <div class="itens">
        <input type="password" name="" id="" placeholder="Confirmar Senha" v-model="user.confirmarSenha" />
      </div>
      <div class="itens">
        <input type="date" name="" id="" placeholder="Data de Nascimento" v-model="user.dataNascimento" />
      </div>
      <div class="itens">
        <input type="text" name="" id="" placeholder="Endereço" v-model="user.endereco" />
      </div>
      <div class="itens">
        <input type="text" name="" id="" placeholder="Cidade" v-model="user.cidade" />
      </div>
      <div class="itens">
        <select name="" id="" v-model="user.estado">
          <option v-for="estado in user.estado" :key="estado" :value="estado">{{ estado }}</option>
        </select>
      </div>
      <div class="itens"><button @click="envia = true">Enviar</button></div>
    </form>
  </div>
  <div v-if="envia == true" class="container corDados">
    <div class="cabecalhoDados"><h1>Seus dados</h1> <button @click="envia = false">X</button></div>
    <p>Nome: {{ user.nome }}</p>
    <p>Email: {{ user.email }}</p>
    <p>Senha: {{ user.senha }}</p>
    <p>Confirmar Senha: {{ user.confirmarSenha }}</p>
    <p>Data de Nascimento: {{ user.dataNascimento }}</p>
    <p>Endereço: {{ user.endereco }}</p>
    <p>Cidade: {{ user.cidade }}</p>
    <p>Estado: {{ user.estado }}</p>
  </div>
</template>

<style scoped></style>
