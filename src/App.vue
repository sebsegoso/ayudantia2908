
<script>
import { shallowRef } from 'vue'
import PresentaDiapos from './components/PresentaDiapos.vue'
import DirectivasCondicionales from './components/DirectivasCondicionales.vue'
import VFor from './components/VFor.vue'
import VBind from './components/VBind.vue'
import ManejoEventos from './components/ManejoEventos.vue'
import ParentComponent from './components/ejemploComponentes/ParentComponent.vue'
import ToDoEmits from './components/propsYEmits/ToDoEmits.vue'

export default {
  components: { ToDoEmits, DirectivasCondicionales, VFor, VBind, PresentaDiapos },
  data() {
    return {
      sections: [
        { buttonText: 'Directivas condicionales', component: shallowRef(DirectivasCondicionales) },
        { buttonText: 'Uso de v-for', component: shallowRef(VFor) },
        { buttonText: 'V-bind', component: shallowRef(VBind) },
        { buttonText: 'Manejo de eventos', component: shallowRef(ManejoEventos) },
        { buttonText: 'Componentes', component: shallowRef(ParentComponent) },
        { buttonText: 'Props y Emit', component: shallowRef(ToDoEmits) }
      ]
    }
  }
}
</script>

<template>
  <PresentaDiapos :sections="sections" />
</template>