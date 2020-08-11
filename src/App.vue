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
        opciones: [
          {
            id: 1,
            texto: "Lima",
            descripcion:
              "Lima es la capital de Perú ubicada en la árida costa del Pacífico del país."
          },
          {
            id: 2,
            texto: "Arequipa",
            descripcion:
              "Arequipa es la capital de la época colonial de la región de Arequipa en Perú."
          },
          {
            id: 3,
            texto: "Loreto",
            descripcion:
              "Loreto es un departamento del Perú situado en el noreste del país, en la Amazonía peruana. "
          },
          {
            id: 4,
            texto: "Tacna",
            descripcion:
              "Tacna es una ciudad del sur de Perú, cerca de la frontera con Chile. "
          }
        ]
      }
    };
  }
};
</script>
