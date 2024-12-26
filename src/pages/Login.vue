<template>
  <div class="background-container">
    <div class="login-box">
      <h4>Iniciar Sesión</h4>
      <q-input
        filled
        outlined
        v-model="email"
        label="Correo Electrónico"
        type="email"
      />
      <q-input
        filled
        outlined
        v-model="password"
        label="Contraseña"
        type="password"
      />
      <q-btn label="Ingresar" color="primary" @click="handleLogin" />
      <q-btn flat label="¿Olvidaste tu contraseña?" @click="recoverPassword" />
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import { useRouter } from "vue-router";
import { Notify } from "quasar";
const email = ref("");
const password = ref("");
const router = useRouter();
const validateEmail = (email) => {
  const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
  return emailPattern.test(email);
};
const handleLogin = () => {
  // Lógica para manejar el inicio de sesión
  // console.log('Iniciando sesión con:', email.value, password.value);
  if (!email.value) {
    Notify.create({
      message: "El correo electrónico no puede estar vacío.",
      color: "negative",
      position: "top",
      timeout: 3000,
    });
    return;
  } else if (!validateEmail(email.value)) {
    Notify.create({
      message: "El formato del correo electrónico no es válido.",
      color: "negative",
      position: "top",
      timeout: 3000,
    });
    return;
  }

  // Validar que la contraseña no esté vacía

  if (!password.value) {
    Notify.create({
      message: "La contraseña no puede estar vacía.",
      color: "negative",
      position: "top",
      timeout: 3000,
    });
    return;
  }
  Notify.create({
    message: "Ingresó correctamente",
    color: "positive", // Puedes usar 'negative', 'warning', 'info', etc.
    position: "top", // Posición de la notificación
    timeout: 3000, // Duración en milisegundos
  });
  router.push("/inicio");
};

const recoverPassword = () => {
  // Lógica para recuperar la contraseña
  console.log("Recuperar contraseña");
};
</script>

<style lang="scss" scoped>
.background-container {
  background-image: url("/img/fondo3.jpg"); /* Ruta a tu imagen */
  background-size: cover; /* Asegura que la imagen cubra todo el contenedor */
  background-position: center; /* Centra la imagen */
  height: 100vh; /* Altura del contenedor */
  display: flex;
  justify-content: center; /* Centra el contenido horizontalmente */
  align-items: center; /* Centra el contenido verticalmente */
}

.login-box {
  background-color: white; /* Color de fondo blanco */
  padding: 20px; /* Espaciado interno */
  border-radius: 8px; /* Bordes redondeados */
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1); /* Sombra para el recuadro */
  width: 300px; /* Ancho del recuadro */
  text-align: center; /* Centra el texto */
}

h2 {
  margin-bottom: 20px; /* Espaciado inferior del título */
}
</style>
