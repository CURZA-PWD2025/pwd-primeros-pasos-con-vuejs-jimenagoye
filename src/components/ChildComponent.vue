<template>
  <div class="container">
    <h1>Crear Usuario</h1>
    <form @submit.prevent="crearUsuario">
      <label>Nombre de Usuario:</label>
      <input type="text" v-model="nombre" required />

      <label>Email:</label>
      <input type="email" v-model="email" required />

      <label>Password:</label>
      <input type="password" v-model="password" required />

      <label>Fecha de Nacimiento:</label>
      <input type="date" v-model="fechaNacimiento" required />

      <button type="submit">Crear Usuario</button>
    </form>

    <div v-if="nombre || email || fechaNacimiento">
      <h2>Vista Previa del Usuario</h2>
      <p><strong>Nombre:</strong> {{ nombre }}</p>
      <p><strong>Email:</strong> {{ email }}</p>
      <p><strong>Fecha de Nacimiento:</strong> {{ fechaNacimiento }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

export default defineComponent({
  setup() {
    const nombre = ref("");
    const email = ref("");
    const password = ref("");
    const fechaNacimiento = ref("");

    const calcularEdad = (fechaNacimiento: string): number => {
      const hoy = new Date();
      const nacimiento = new Date(fechaNacimiento);
      let edad = hoy.getFullYear() - nacimiento.getFullYear();
      const mes = hoy.getMonth() - nacimiento.getMonth();
      if (mes < 0 || (mes === 0 && hoy.getDate() < nacimiento.getDate())) {
        edad--;
      }
      return edad;
    };

    const crearUsuario = () => {
      if (!nombre.value || !email.value || !fechaNacimiento.value) {
        alert("Por favor, completa todos los campos.");
        return;
      }

      const usuario = {
        nombre: nombre.value,
        email: email.value,
        password: password.value,
        fechaNacimiento: fechaNacimiento.value,
        edad: calcularEdad(fechaNacimiento.value),
      };

      console.log("Usuario registrado:", usuario);

      alert(`Usuario creado con éxito!\n\nNombre: ${usuario.nombre}\nEmail: ${usuario.email}\nEdad: ${usuario.edad} años`);

      nombre.value = "";
      email.value = "";
      password.value = "";
      fechaNacimiento.value = "";
    };

    return {
      nombre,
      email,
      password,
      fechaNacimiento,
      crearUsuario,
    };
  },
});
</script>

<style scoped>
.container {
  width: 400px;
  margin: 50px auto 50px 30px;
  padding: 35px;
  border-radius: 10px;
  background-color: #e0bacd;
  box-shadow: 0 4px 8px rgba(0,0,0,0.1);
}
label {
  display: block;
  margin-top: 10px;
}
input, button {
  width: 95%;
  margin-top: 5px;
  padding: 10px;
  font-size: 16px;
}
button {
  background-color: #ab4089;
  color: rgb(250, 249, 249);
  border: none;
  border-radius: 5px;
  margin-top: 20px;
}
button:hover {
  background-color: #b62068;
}
</style>