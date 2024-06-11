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
  ],
  hobbies: [],
  linguagens: [],
  biografia: ''
})
let envia = ref(false)
let hobbie = ""
let linguagem = ref('')
const addHobbie = () => {
  user.hobbies.push(hobbie)
  hobbie = "" 
}
const addLinguagem = () => {
  user.linguagens.push(linguagem)
  linguagem.value = ''
}
</script>

<template>
  <div class="container">
    <h1>Insira seus dados de usuário</h1>
    <form action="" @submit.prevent>
      <div class="itens">
        <label for="nameinput">Nome:</label>
        <input type="text" name="nameinput" id="" placeholder='Ex: "Marco"' v-model="user.nome" />
      </div>
      <div class="itens">
        <label for="emailinput">Email:</label>
        <input type="email" name="emailinput" id="" placeholder='Ex: "andre@..."' v-model="user.email" />
      </div>
      <div class="itens">
        <label for="passwordinput">Senha:</label>
        <input type="password" name="passwordinput" id="" placeholder='**********' v-model="user.senha" />
      </div>
      <div class="itens">
        <label for="confirmpassword">Confirmar:</label>
        <input type="password" name="confirmpassword" id="" placeholder="**********" v-model="user.confirmarSenha" />
      </div>
      <div class="itens">
        <label for="dateinput">Data de nascimento:</label>
        <input type="date" name="dateinput" id="" placeholder='Ex: "01/01/2001"' v-model="user.dataNascimento" />
      </div>
      <div class="itens">
        <label for="addressinput">Endereço:</label>
        <input type="text" name="addressinput" id="" placeholder='Ex: "Rua..."' v-model="user.endereco" />
      </div>
      <div class="itens">
        <label for="cityinput">Cidade:</label>
        <input type="text" name="cityinput" id="" placeholder='Ex: "Araquari"' v-model="user.cidade" />
      </div>
      <div class="itens">
        <label for="hobbiesinput">Hobbies:</label>
        <input type="text" name="hobbiesinput" id="" placeholder='Ex: "correr"' v-model="hobbie"/>
        <button @click="addHobbie">add</button>
      </div>
      <div class="itens">
        <label for="languagesinput">Linguagens:</label>
        <input type="text" name="languagesinput" id="" placeholder='Ex: "Inglês"' v-model="linguagem" />
        <button @click="addLinguagem">add</button>
      </div>
      <div class="itens">
        <label for="stateInput">Estado:</label>
        <select name="stateInput" id="" v-model="user.estado">
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
    <p>Hobbies: <p v-for="hobbiee in user.hobbies" :key="hobbiee">{{ hobbiee }}</p></p>
    <p>Linguagens: {{ user.linguagens }}</p>
  </div>
</template>

<style scoped>
.container{
  margin:3rem auto;
  width: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: #f9f9f9;
}
form{
  margin: auto;
  width: 60%;
}
.itens{
  margin: 1rem auto;
  width: 70%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  /* flex-direction: column; */
}
.itens > input{
  width: 70%;
  padding: 0.5rem;
  border-radius: 0.5rem;
  border: 1px solid #ccc;
}
.itens >label{
  width: 30%;
}
.itens >  button:nth-child(3){
  background-color: #4CAF50;
  margin-left: .25rem;
  padding: 0.5rem;
  border-radius: 0.5rem;
  border: 1px solid #ccc;
}
.itens> select {
  width: 70%;
  padding: 0.5rem;
  border-radius: 0.5rem;
  border: 1px solid #ccc;
}
.itens > button:only-child{
  margin: auto;
  background-color: aqua;
  padding: 0.5rem;
  border-radius: 0.5rem;
  border: 1px solid black;
}
.container h1{
  margin-bottom: 1rem;
  font-family: Verdana, Geneva, Tahoma, sans-serif;
}
</style>
