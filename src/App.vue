<template>
  <div class="tarea-lista">
    <h1>{{tareas.length}} TAREAS</h1>
    <form class="form" @submit.prevent="crearTarea">
      <label class="label" for="tarea">Tarea Nueva:</label>
      <input class="input" type="text" v-model="nuevaTarea" id="tarea" />
      <input class="button" type="submit" value="Crear tarea" />
    </form>
    <ol class="lista">
      <li
        class="tarea"
        v-for="(tarea, x) in tareas"
        :key="'tarea' + x"
        :class="{complete: tarea.complete}"
        @click="completeTarea(tarea.text)"
      >{{tarea.text}}</li>
    </ol>
  </div>
</template>

<script>
export default {
  data: () => ({
    nuevaTarea: "",
    tareas: []
  }),
  methods: {
    crearTarea() {
      let tarea = {
        text: this.nuevaTarea,
        complete: false
      };
      this.tareas.push(tarea);
      this.nuevaTarea = "";
      console.log(this.tareas);
    },
    completeTarea(tareaTexto) {
      for (let x = 0; x < this.tareas.length; x++) {
        let tarea = this.tareas[x];
        if (tareaTexto === tarea.text) {
          tarea.complete = !tarea.complete;
        }
      }
    }
  }
};
</script>
<style scoped>
.tarea-lista {
  width: 800px;
  max-width: 100%;
  margin: 0px auto;
}
.form {
  background: orangered;
  border-radius: 12px;
  padding: 30px;
  box-shadow: 0px 10px 22px -1px rgba(0,0,0,0.25);
  margin-top: 10px;
}
.label {
  display: block;
  margin-bottom: 10px;
  font-weight: bold;
  
}
.input {
  height: 35px;
}
.button {
  margin-left: 20px;
  height: 35px;
  border: none;
  border-radius: 5px;
  box-shadow: 0 1px 4px rgba(0, 0, 0, .2);
  background-color: black;
  color: yellow;
  cursor: pointer
}
.lista {
  margin-top: 40px;
}
.tarea {
  cursor: pointer;
  margin: 10px 0;
}
.complete {
  text-decoration: line-through;
  color: lightgrey;
}

</style>
