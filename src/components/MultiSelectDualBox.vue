<template>
  <v-container>
    <v-row>
      <v-col cols="12" sm="12" md="12" lg="12">
        <v-card>
          <v-card-text>
            <v-row align="center" justify="center">
              <v-col cols="12" sm="6" md="6" lg="6">
                <v-text-field
                  dense
                  outlined
                  v-model="buscadorOpciones"
                  clearable
                  :label="options.buscadorTexto1"
                ></v-text-field>
              </v-col>
              <v-col cols="12" sm="6" md="6" lg="6">
                <v-text-field
                  dense
                  outlined
                  v-model="buscadorSeleccionados"
                  clearable
                  :label="options.buscadorTexto2"
                ></v-text-field>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12" sm="6" md="6" lg="6">
                <v-list
                  shaped
                  rounded
                  dense
                  style="max-height: 225px"
                  class="overflow-y-auto"
                  v-if="filtrarOpciones.length"
                >
                  <v-subheader>{{options.subHeader1}}</v-subheader>
                  <v-list-item-group>
                    <v-list-item
                      two-line
                      v-for="o in filtrarOpciones"
                      :key="o.texto"
                      @click="moverDerecha(options.opciones.indexOf(o))"
                    >
                      <v-list-item-content>
                        <v-list-item-title>{{o.texto}}</v-list-item-title>
                        <v-list-item-subtitle>{{o.descripcion}}</v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </v-list-item-group>
                </v-list>
                <v-list v-else class="d-flex justify-center">
                  <p class="text--disabled text-center">{{options.noData1}}</p>
                </v-list>
              </v-col>
              <v-col cols="12" sm="6" md="6" lg="6">
                <v-list
                  dense
                  shaped
                  rounded
                  style="max-height: 225px"
                  class="overflow-y-auto"
                  v-if="filtrarSeleccionados.length"
                >
                  <v-subheader>{{options.subHeader2}}</v-subheader>
                  <v-list-item-group>
                    <v-list-item
                      two-line
                      v-for="s in filtrarSeleccionados"
                      :key="s.texto"
                      @click="moverIzquierda(options.seleccionados.indexOf(s))"
                    >
                      <v-list-item-content>
                        <v-list-item-title>{{s.texto}}</v-list-item-title>
                        <v-list-item-subtitle>{{s.descripcion}}</v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </v-list-item-group>
                </v-list>
                <v-list v-else class="d-flex justify-center">
                  <p class="text--disabled text-center">{{options.noData2}}</p>
                </v-list>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12" sm="6" md="6" lg="6" class="d-flex justify-center">
                <v-btn v-bind="size" @click="moverDerecha(-1)">
                  Mover todo a la derecha
                  <v-icon>mdi-chevron-double-right</v-icon>
                </v-btn>
              </v-col>
              <v-col cols="12" sm="6" md="6" lg="6" class="d-flex justify-center">
                <v-btn v-bind="size" @click="moverIzquierda(-1)">
                  <v-icon>mdi-chevron-double-left</v-icon>Mover todo a la izquierda
                </v-btn>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>


<script>
export default {
  name: "VueMultiSelectDualListBox",
  props: ["options"],
  data() {
    return {
      seleccionados: [],
      opciones: [],
      buscadorOpciones: "",
      buscadorSeleccionados: ""
    };
  },
  methods: {
    moverDerecha(index) {
      let vue = this;
      if (index >= 0) {
        vue.options.seleccionados.push(vue.options.opciones[index]);
        vue.options.opciones.splice(index, 1);
      } else {
        for (var cont = 0; cont < vue.options.opciones.length; cont++) {
          vue.options.seleccionados.push(vue.options.opciones[cont]);
        }

        vue.options.opciones.splice(0, vue.options.opciones.length);
      }
    },
    moverIzquierda(index) {
      let vue = this;
      if (index >= 0) {
        vue.options.opciones.push(vue.options.seleccionados[index]);
        vue.options.seleccionados.splice(index, 1);
        return;
      }

      for (var cont = 0; cont < vue.options.seleccionados.length; cont++) {
        vue.options.opciones.push(vue.options.seleccionados[cont]);
      }
      vue.options.seleccionados.splice(0, vue.options.seleccionados.length);
    }
  },
  computed: {
    filtrarOpciones() {
      let vue = this;

      if (vue.buscadorOpciones) {
        return vue.options.opciones.filter(item => {
          return item.texto.toLowerCase().indexOf(vue.buscadorOpciones) !== -1;
        });
      }
      return vue.options.opciones;
    },
    filtrarSeleccionados() {
      let vue = this;

      if (vue.buscadorSeleccionados) {
        return vue.options.seleccionados.filter(item => {
          return (
            item.texto.toLowerCase().indexOf(vue.buscadorSeleccionados) !== -1
          );
        });
      }
      return vue.options.seleccionados;
    },
    size() {
      const size = { xs: "x-small", sm: "small", lg: "large", xl: "x-large" }[
        this.$vuetify.breakpoint.name
      ];
      return size ? { [size]: true } : {};
    }
  }
};
</script>
