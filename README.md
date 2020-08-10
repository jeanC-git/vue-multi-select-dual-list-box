# vuemultiselectduallistbox

### NPM package
[vuemultiselectduallistbox](https://www.npmjs.com/package/vue-multi-select-dual-box/v/0.1.0).

## Instalación del componente /Component installation

### Vía npm / via npm

```
npm i vue-multi-select-dual-box --save
```

### Uso / Use

```
En tu componente de vue:

import { MultiSelectDualBox } from "vue-multi-select-dual-box";
export default {
  components: {
    MultiSelectDualBox
  },
....

```
### Luego en tu template tag / Them in your template tag

```
<MultiSelectDualBox :options="options"></MultiSelectDualBox>
....


### Bind de opciones / Bind options
```
options: {
    buscadorTexto1: "buscadorTexto1", // Placeholder del input 1 / Placeholder from input 1
    buscadorTexto2: "buscadorTexto2", // Placeholder del input 2 / Placeholder from input 2
    subHeader1: "subHeader1", // Subheader del box 1 / Subheader from box 1
    subHeader2: "subHeader2", // Subheader del box 2 / Subheader from box 2
    noData1:
        "noData1", // Texto que se muestra cuando no hay elementos en la lista 1 / Text displayed when there are no items in list 1
    noData2:
        "noData2", // Texto que se muestra cuando no hay elementos en la lista 2 / Text displayed when there are no items in list 2
    seleccionados: [], // Array de elementos pre seleccionados (lista 2) / Array of pre-selected elements (list 2)
    opciones: [] // Array de opciones (lista 1) / Array of options (list 1)
    }
```


