<template>
  <div class="formulario-actas">
      <h1>Información del acta</h1>
      <div class="form">
      <form action="">
          <div class="informacion-acta">
          <div>
              <label for="fecha">Fecha</label>
              <input type="date" id="fecha" v-model="fecha" />
          </div>
          <div>
              <label for="horaInicio">Hora De Inicio</label>
              <input type="time" id="horaInicio" v-model="horaInicio" />
          </div>
          <div>
              <label for="horaFin">Hora De Finalización</label>
              <input type="time" id="horaFin" v-model="horaFin" />
          </div>
          <div>
              <label for="asunto">Asunto</label>
              <input type="text" id="asunto" v-model="asunto" />
          </div>
          </div>
          <div class="agregar-puntos">
          <h1>Agrega los puntos de tu reunión aquí!</h1>
          <div v-for="(punto, index) in puntos" :key="index">
              <p v-if="!punto.editar" @click="editarPunto(index)">{{ index + 1 }}. {{ punto.contenido }}</p>
              <textarea v-else v-model="punto.contenido" @keydown.enter.prevent="guardarPunto(index)"></textarea>
              <!-- <button v-if="!punto.editar" @click="editarPunto(index)">Editar</button> -->
              <button v-if="!punto.editar" @click="eliminarPunto(index)">Eliminar</button>
          </div>
          <div>
            <textarea v-model="inputPunto" @keydown.enter.prevent="agregarPunto"></textarea>
          </div>
          </div>
          <button type="submit" @click.prevent="submitForm">Enviar</button>
      </form>
      </div>
  </div>
  </template>
  
  <script>
  export default {
  data() {
      return {
      fecha: '',
      horaInicio: '',
      horaFin: '',
      asunto: '',
      lugar: '',
      inputPunto: '',
      puntos: []
      }
  },
  methods: {
      agregarPunto() {
      this.puntos.push({ contenido: this.inputPunto, editar: false });
      this.inputPunto = '';
      },
      editarPunto(index) {
      this.puntos[index].editar = true;
      },
      guardarPunto(index) {
      this.puntos[index].editar = false;
      },
      eliminarPunto(index) {
      this.puntos.splice(index, 1);
      },
      submitForm() {
      console.log("Datos del formulario: ", this.fecha, this.horaInicio, this.horaFin, this.asunto, this.lugar, this.puntos);
      }
  }
  };
  </script>  