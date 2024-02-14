<template>
  <div class="container">
   
    <div class="row justify-content-center">
      <div class="col-12 col-md-8 col-lg-6 pb-5">
        <!--Form with header-->

        <form @submit.prevent="enviarFormulario">
          <div class="card border-primary rounded-0">
            <div class="card-header p-0">
              <div class="bg-info text-white text-center py-2">
                <h3><i class="fa fa-envelope"></i> Contactanos</h3>
                <p class="m-0">Con gusto te ayudaremos</p>
              </div>
            </div>
            <div class="card-body p-3">
              <!--Body-->
              <div class="form-group">
                <div class="input-group mb-2">
                  <div class="input-group-prepend">
                    <div class="input-group-text">
                      <i class="fa fa-user text-info"></i>
                    </div>
                  </div>
                  <input
                    type="text"
                    v-model="formulario.nombre"
                    class="form-control"
                    id="nombre"
                    name="nombre"
                    placeholder="Nombre y Apellido"
                    required
                  />
                </div>
              </div>
              
              <div class="form-group">
                <div class="input-group mb-2">
                  <div class="input-group-prepend">
                    <div class="input-group-text">
                      <i class="fa fa-user text-info"></i>
                    </div>
                  </div>
                  <input
                    type="int"
                    v-model="formulario.cedula"
                    class="form-control"
                    id="nombre"
                    name="cedula"
                    placeholder="Ingrese su cedula"
                    required
                  />
                </div>
              </div>
              <div class="form-group">
                <div class="input-group mb-2">
                  <div class="input-group-prepend">
                    <div class="input-group-text">
                      <i class="fa fa-envelope text-info"></i>
                    </div>
                  </div>
                  <input
                    type="text"
                    v-model="formulario.correoElectronico"
                    class="form-control"
                    id="nombre"
                    name="email"
                    placeholder="ejemplo@mail.com"
                    required
                  />
                </div>
              </div>
              <div class="form-group">
                <div class="input-group mb-2">
                  <div class="input-group-prepend">
                    <div class="input-group-text">
                      <i class="fa fa-hospital text-info"></i>
                    </div>
                  </div>
                  <!-- <input
                    type="text"
                    v-model="formulario.sede"
                    class="form-control"
                    id="nombre"
                    name="sede"
                    placeholder="Sede"
                    required
                  /> -->
                  <input list= "opciones" id="nombre" v-model="formulario.sede" class="form-control" name="sede" placeholder="Sede" required>
                  <datalist id="opciones">
                  <option >Kennedy</option>
                  <option >Urdesa</option>
                  <option >Samborondon</option>
                  </datalist>
                </div>
              </div>
              <div class="form-group">
                <div class="input-group mb-2">
                  <div class="input-group-prepend">
                    <div class="input-group-text">
                      <i class="fa fa-user text-info"></i>
                    </div>
                  </div>
                  <input
                    type="text"
                    v-model="formulario.nombreMedico"
                    class="form-control"
                    id="nombre"
                    name="medico"
                    placeholder="Nombre del Medico"
                    required
                  />
                </div>
              </div>
              <div class="form-group">
                <div class="input-group mb-2">
                  <div class="input-group-prepend">
                    <div class="input-group-text">
                      <i class="fa fa-clipboard text-info"></i>
                    </div>
                  </div>
                  <input
                    type="int"
                    v-model="formulario.especialidad"
                    class="form-control"
                    id="nombre"
                    name="especialidad"
                    placeholder="Especialidad"
                    required
                  />
                </div>
              </div>
              

              <div class="form-group">
                <div class="input-group mb-2">
                  <div class="input-group-prepend">
                    <div class="input-group-text">
                      <i class="fa fa-comment text-info"></i>
                    </div>
                  </div>
                  <input
                    type="text"
                    v-model="formulario.observacion"
                    class="form-control"
                    placeholder="Escriba su observacion"
                    required
                  >
                </div>
              </div>

              <div class="text-center">
                <input
                  type="submit"
                  value="Enviar"
                  class="btn btn-info btn-block rounded-0 py-2"
                />
              </div>
            </div>
          </div>
        </form>
        <!--Form with header-->
      </div>
    </div>
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
}

</script>



