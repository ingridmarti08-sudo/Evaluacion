<template>
  <div class="registro-form">
    <h2>Registro</h2>
    <form @submit.prevent="registrarUsuario">
      <input type="text" v-model="nombre" placeholder="Nombre" required />
      <input type="text" v-model="apellido" placeholder="Apellido" required />
      <input type="email" v-model="email" placeholder="Correo electrónico" required />
      <input type="tel" v-model="telefono" placeholder="Teléfono" required />
      <input type="password" v-model="password" placeholder="Contraseña" required />
      <input type="password" v-model="confirmarPassword" placeholder="Confirmar contraseña" required />
      <button type="submit">Registrarse</button>
    </form>
    <p v-if="mensaje" class="mensaje">{{ mensaje }}</p>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const nombre = ref('')
const apellido = ref('')
const email = ref('')
const telefono = ref('')
const password = ref('')
const confirmarPassword = ref('')
const mensaje = ref('')

const registrarUsuario = () => {
  if (password.value !== confirmarPassword.value) {
    mensaje.value = "Las contraseñas no coinciden"
    return
  }

  mensaje.value = `Usuario ${nombre.value} ${apellido.value} registrado con éxito`
  
  // Limpiar campos
  nombre.value = ''
  apellido.value = ''
  email.value = ''
  telefono.value = ''
  password.value = ''
  confirmarPassword.value = ''
}
</script>

<style scoped>
body {
  margin: 0;
  font-family: 'Arial', sans-serif;
  background-color: #e0f7fa;
}

.registro-form {
  width: 100%;
  max-width: 360px;
  margin: 60px auto;
  padding: 25px;
  border-radius: 15px;
  background: linear-gradient(135deg, #6dd5fa, #2980b9);
  box-shadow: 0 8px 20px rgba(0,0,0,0.2);
  color: #fff;
  text-align: center;
  box-sizing: border-box;
}

h2 {
  margin-bottom: 20px;
  font-size: 26px;
}

form {
  display: flex;
  flex-direction: column;
  gap: 15px;
}

input {
  width: 100%;
  padding: 12px 15px;
  border: none;
  border-radius: 10px;
  outline: none;
  box-sizing: border-box;
  font-size: 16px;
  transition: all 0.3s;
}

input:focus {
  box-shadow: 0 0 8px #fff;
}

button {
  width: 100%;
  padding: 12px;
  background: linear-gradient(90deg, #00c6ff, #0072ff);
  border: none;
  border-radius: 10px;
  color: #fff;
  font-weight: bold;
  cursor: pointer;
  transition: all 0.3s;
}

button:hover {
  transform: scale(1.05);
  box-shadow: 0 5px 15px rgba(0,0,0,0.3);
}

.mensaje {
  margin-top: 15px;
  font-weight: bold;
  color: #ffd700;
}
</style>
