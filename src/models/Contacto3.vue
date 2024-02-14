<template>

  <div>
    <h2>Formulario de Contacto</h2>
    <form @submit.prevent="enviarFormulario">
      <div>
        <label>Nombre:</label>
        <input type="text" v-model="formulario.nombre" required>
      </div>
      <div>
        <label>Cedula:</label>
        <input type="int" v-model="formulario.cedula" required>
      </div>
      <div>
        <label>Correo Electronico:</label>
        <input type="text" v-model="formulario.correoElectronico" required>
      </div>
      <div>
        <label>Sede:</label>
        <input type="text" v-model="formulario.sede" required>
      </div>
      <div>
        <label>Medico:</label>
        <input type="text" v-model="formulario.nombreMedico" required>
      </div>
      <div>
        <label>Especialidad:</label>
        <input type="text" v-model="formulario.especialidad" required>
      </div>
      <div>
        <label>Observacion:</label>
        <input type="text" v-model="formulario.observacion" required>
      </div>
      <!-- Agrega más campos del formulario aquí -->
      <button type="submit">Enviar</button>
    </form>
  </div>

</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      formulario: {
        nombre: '',
        // Agrega más campos del formulario aquí
      }
    };
  },
  methods: {
    enviarFormulario() {
      axios.post('http://localhost:8080/api/contacto', this.formulario)
        .then(response => {
          console.log('Datos enviados correctamente:', response.data);
          // Aquí puedes manejar la respuesta del servidor si es necesario
        })
        .catch(error => {
          console.error('Error al enviar datos:', error);
        });
    }
  }
};
</script>



<style>
</style>