<script setup>
import { ref, reactive, onMounted } from "vue";

const user = reactive({
  email: "",
  senha: "",
});

const names = reactive([]);

onMounted(() => {
  //assim q o loginview(componente pagina do login) for startado, esse componente gerado
  names: ({
    Firstname: "",
  });
});

function login() {
  console.log(user.email, user.senha);
  names.push({
    Firstname: user.email,
  });
}

function remove(user) {
  const index = names.findIndex(name => {
    return name.Firstname == user.Firstname;
  });
  names.splice(index, 1);
}
</script>
<template>
  <template v-if="names.length > 0">
    <ul>
      <li v-for="name in names">
        {{ name.Firstname }} - <button @click="remove(name)">remover</button>
      </li>
    </ul>
  </template>
  <template v-else>Nenhum usuario cadastrado</template> <br />

  <template v-if="user.email.length <= 0">Email vazio</template>
  <template v-else>Email {{ user.email }}</template> <br />
  <template v-if="user.senha.length <= 0">Senha vazia</template>
  <template v-else>senha {{ user.senha }}</template>
  <form action="" @submit.prevent="login">
    <input type="text" placeholder="Email" v-model="user.email" /> <br />
    <input type="text" placeholder="senha" v-model="user.senha" /> <br />
    <button type="submit">Enviar</button>
  </form>
</template>
