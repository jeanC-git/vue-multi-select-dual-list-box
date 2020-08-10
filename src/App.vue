<template>
  <v-app>
    <v-dual-select-box :options="options" />
  </v-app>
</template>

<script>
import VDualSelectBox from "./components/MultiSelectDualBox";
export default {
  name: "App",

  components: {
    VDualSelectBox
  },

  data() {
    return {
      options: {
        buscadorTexto1: "Buscar permisos disponibles",
        buscadorTexto2: "Buscar permisos actuales",
        subHeader1: "Permisos para disponibles para agregar",
        subHeader2: "Permisos actuales",
        noData1:
          "Ya no hay permisos para asignar o la palabra clave no tiene coincidencias.",
        noData2:
          "Aún no hay permisos asignados o la palabra clave no tiene coincidencias.",
        seleccionados: [],
        opciones: []
      }
    };
  }
};
</script>
