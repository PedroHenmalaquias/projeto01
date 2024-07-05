<script setup>
import { ref, reactive } from 'vue'
import { toast } from 'vue3-toastify'
import 'vue3-toastify/dist/index.css'

const user = reactive({
  nome: '',
  email: '',
  senha: '',
  confirmarSenha: '',
  dataNascimento: '',
  endereco: '',
  cidade: '',
  estado: '',
  hobbies: [],
  linguagens: [],
  biografia: ''
})
const estados = [
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
let hobbie = ref('')
let linguagem = ref('')
const addHobbie = () => {
  let hobbieAdd = hobbie.value
  user.hobbies.push(hobbieAdd)
  hobbie.value = ''
}
const addLinguagem = () => {
  let linguagemAdd = linguagem.value
  user.linguagens.push(linguagemAdd)
  linguagem.value = ''
}
const show = ref(false)
function clear() {
  console.log('papo que fpo')
  user.nome = ''
  user.email = ''
  user.senha = ''
  user.confirmarSenha = ''
  user.dataNascimento = ''
  user.endereco = ''
  user.cidade = ''
  user.estado = ''
  user.hobbies = []
  user.linguagens = []
  user.biografia = ''
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
        <input
          type="email"
          name="emailinput"
          id=""
          placeholder='Ex: "andre@..."'
          v-model="user.email"
        />
      </div>
      <div class="itens">
        <label for="passwordinput">Senha:</label>
        <input
          type="password"
          name="passwordinput"
          id=""
          placeholder="**********"
          v-model="user.senha"
        />
      </div>
      <div class="itens">
        <label for="confirmpassword">Confirmar:</label>
        <input
          type="password"
          name="confirmpassword"
          id=""
          placeholder="**********"
          v-model="user.confirmarSenha"
        />
      </div>
      <div class="itens">
        <label for="dateinput">Data de nascimento:</label>
        <input
          type="date"
          name="dateinput"
          id=""
          placeholder='Ex: "01/01/2001"'
          v-model="user.dataNascimento"
        />
      </div>
      <div class="itens">
        <label for="addressinput">Endereço:</label>
        <input
          type="text"
          name="addressinput"
          id=""
          placeholder='Ex: "Rua..."'
          v-model="user.endereco"
        />
      </div>
      <div class="itens">
        <label for="cityinput">Cidade:</label>
        <input
          type="text"
          name="cityinput"
          id=""
          placeholder='Ex: "Araquari"'
          v-model="user.cidade"
        />
      </div>
      <div class="itens">
        <label for="hobbiesinput">Hobbies:</label>
        <input type="text" name="hobbiesinput" id="" placeholder='Ex: "correr"' v-model="hobbie" />
        <button @click="addHobbie">add</button>
      </div>
      <div class="itens">
        <label for="languagesinput">Linguagens:</label>
        <input
          type="text"
          name="languagesinput"
          id=""
          placeholder='Ex: "Inglês"'
          v-model="linguagem"
        />
        <button @click="addLinguagem">add</button>
      </div>
      <div class="itens">
        <label for="stateInput">Estados:</label>
        <select name="stateInput" id="" v-model="user.estado">
          <option v-for="estado in estados" :key="estado">{{ estado }}</option>
        </select>
      </div>
      <div class="itens">
        <button
          @click="
            show = true
            toast.success('Dados enviados com sucesso!', { autoclose: 800 })
          "
        >
          Enviar
        </button>
      </div>
    </form>
  </div>
  <div v-if="show" class="container corDados">
    <div class="cabecalhoDados">
      <h2>Seus dados</h2>
      <button
        @click="
          show = false
          toast.warning('Dados Retirados', { autoclose: 800 })
          clear()
        "
      >
        X
      </button>
    </div>
    <ul>
      <li>Nome: {{ user.nome }}</li>
      <li>Email: {{ user.email }}</li>
      <li>Senha: {{ user.senha }}</li>
      <li>Confirmar Senha: {{ user.confirmarSenha }}</li>
      <li>Data de Nascimento: {{ user.dataNascimento }}</li>
      <li>Endereço: {{ user.endereco }}</li>
      <li>Cidade: {{ user.cidade }}</li>
      <li>Estados: {{ user.estado }}</li>
      <li>
        Hobbies:
        <p v-for="hobbiee in user.hobbies" :key="hobbiee">{{ hobbiee }}</p>
      </li>
      <li>
        Linguagens:
        <p v-for="i in user.linguagens" :key="i">{{ i }}</p>
      </li>
    </ul>
  </div>
</template>
