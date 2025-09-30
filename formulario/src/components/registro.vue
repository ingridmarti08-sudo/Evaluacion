<template>
  <div class="registro-form">
    <h2>Registro</h2>
    <form @submit.prevent="registrarUsuario">
      <input type="text" v-model="nombre" placeholder="Nombre" required />
      <input type="email" v-model="email" placeholder="Correo electrónico" required />
      <input type="password" v-model="password" placeholder="Contraseña" required />
      <button type="submit">Registrarse</button>
    </form>
    <p v-if="mensaje" class="mensaje">{{ mensaje }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const nombre = ref('')
const email = ref('')
const password = ref('')
const mensaje = ref('')

const registrarUsuario = () => {
  mensaje.value = `Usuario ${nombre.value} registrado con éxito`
  nombre.value = ''
  email.value = ''
  password.value = ''
}
</script>

<style scoped>
.registro-form {
  max-width: 350px;
  margin: 50px auto;
  padding: 25px;
  border-radius: 12px;
  box-shadow: 0 4px 15px rgba(0,0,0,0.1);
  background-color: #fff;
  text-align: center;
}

h2 {
  margin-bottom: 20px;
  color: #333;
}

input {
  width: 100%;
  padding: 10px 12px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 8px;
  outline: none;
  transition: border-color 0.3s;
}

input:focus {
  border-color: #4caf50;
}

button {
  width: 100%;
  padding: 10px;
  background-color: #4caf50;
  color: #fff;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  font-weight: bold;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #45a049;
}

.mensaje {
  margin-top: 15px;
  color: #4caf50;
  font-weight: bold;
}
</style>
