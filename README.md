# ayudantia2908

This template should help get you started developing with Vue 3 in Vite.

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Customize configuration

See [Vite Configuration Reference](https://vitejs.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Compile and Minify for Production

```sh
npm run build
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```

# APUNTES

## Desarrollo de Interfaces Interactivas con Vue 3 (Options API)\*\*

### 1. **Directivas de Control de Flujo: v-if, v-else-if, v-else**

#### **Concepto:**

Las directivas `v-if`, `v-else-if`, y `v-else` permiten mostrar u ocultar elementos en el DOM basado en condiciones. Estas condiciones se basan en variables reactivas dentro del estado de un componente.

#### **Ejemplo Completo:**

```vue
<template>
  <div>
    <h2>Bienvenida</h2>
    <p v-if="isLoggedIn">Bienvenido de nuevo, {{ username }}.</p>
    <p v-else-if="isGuest">Bienvenido, invitado.</p>
    <p v-else>Por favor, inicia sesión para continuar.</p>

    <button @click="toggleLogin">
      {{ isLoggedIn ? 'Cerrar Sesión' : 'Iniciar Sesión' }}
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isLoggedIn: false,
      isGuest: false,
      username: 'Pepito'
    }
  },
  methods: {
    toggleLogin() {
      this.isLoggedIn = !this.isLoggedIn
      this.isGuest = !this.isLoggedIn
    }
  }
}
</script>
```

#### **Explicación:**

- **Estado**: Declaramos las variables `isLoggedIn`, `isGuest`, y `username` dentro de `data()` para gestionar el estado del componente.
- **Condicionales**: `v-if` muestra un mensaje si el usuario está conectado, `v-else-if` muestra un mensaje de bienvenida al invitado, y `v-else` pide al usuario que inicie sesión.
- **Método**: `toggleLogin` permite alternar entre los estados de sesión activa y de invitado.

#### **Ejemplo de Uso Cotidiano:**

En una aplicación de comercio electrónico, podrías usar `v-if` para mostrar diferentes mensajes de bienvenida o mostrar un botón de "Iniciar Sesión" si el usuario no ha iniciado sesión.

---

### 2. **Directiva v-for**

#### **Concepto:**

`v-for` permite iterar sobre listas de datos y renderizar elementos del DOM para cada elemento de la lista.

#### **Ejemplo Completo:**

```vue
<template>
  <div>
    <h2>Lista de Tareas</h2>
    <ul>
      <li v-for="(task, index) in tasks" :key="task.id">
        {{ index + 1 }}. {{ task.title }}
        <button @click="removeTask(index)">Eliminar</button>
      </li>
    </ul>
    <button @click="addTask">Agregar Tarea</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        { id: 1, title: 'Estudiar Vue.js' },
        { id: 2, title: 'Desarrollar una aplicación' },
        { id: 3, title: 'Preparar la presentación' }
      ]
    }
  },
  methods: {
    addTask() {
      const newTask = { id: Date.now(), title: 'Nueva Tarea' }
      this.tasks.push(newTask)
    },
    removeTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>
```

#### **Explicación:**

- **Estado**: Declaramos una lista de tareas en `data()`.
- **Iteración**: `v-for` itera sobre el array `tasks`, renderizando cada tarea en una lista ordenada.
- **Métodos**: `addTask` agrega una nueva tarea y `removeTask` elimina la tarea seleccionada por índice.

---

### 3. **v-bind (alias `:`)**

#### **Concepto:**

`v-bind` permite enlazar atributos del DOM a propiedades del componente Vue de forma reactiva.

#### **Ejemplo Completo:**

```vue
<template>
  <div>
    <h2>Galería de Imágenes</h2>
    <img :src="imageUrl" :alt="imageDescription" />
    <button @click="changeImage">Cambiar Imagen</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      imageUrl: 'https://via.placeholder.com/150',
      imageDescription: 'Imagen de ejemplo'
    }
  },
  methods: {
    changeImage() {
      this.imageUrl = 'https://via.placeholder.com/200'
      this.imageDescription = 'Nueva imagen de ejemplo'
    }
  }
}
</script>
```

#### **Explicación:**

- **Estado**: `imageUrl` y `imageDescription` son propiedades que controlan la URL de la imagen y su descripción.
- **Enlace Reactivo**: `v-bind` (o `:`) enlaza `src` y `alt` al estado del componente, actualizándose automáticamente cuando cambia el estado.

#### **Ejemplo de Uso Cotidiano:**

Usa `v-bind` para crear galerías de productos en una tienda online, donde la imagen, descripción y precio del producto se actualizan dinámicamente.

---

### 4. **Manejo de Eventos**

#### **Concepto:**

El manejo de eventos en Vue se realiza con la directiva `v-on` (alias `@`), que permite escuchar y responder a eventos del DOM como clics, envíos de formularios, entre otros.

#### **Ejemplo Completo:**

```vue
<template>
  <div>
    <h2>Contador de Clics</h2>
    <p>Número de clics: {{ counter }}</p>
    <button @click="incrementCounter">Haz clic aquí</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      counter: 0
    }
  },
  methods: {
    incrementCounter() {
      this.counter++
    }
  }
}
</script>
```

#### **Explicación:**

- **Estado**: `counter` es una variable reactiva que mantiene el conteo de clics.
- **Eventos**: `v-on:click` (alias `@click`) escucha el evento de clic en el botón y ejecuta `incrementCounter`, que incrementa el contador.

#### **Ejemplo de Uso Cotidiano:**

En un formulario de contacto, podrías usar `v-on` para manejar la lógica de validación y envío del formulario.

---

### 5. **Creación y Uso de Componentes**

#### **Concepto:**

Los componentes en Vue son bloques reutilizables de UI que encapsulan HTML, CSS, y JavaScript, facilitando la creación de interfaces modulares.

#### **Ejemplo Completo:**

**Componente Padre (ParentComponent.vue):**

```vue
<template>
  <div>
    <h2>Tarjetas de Producto</h2>
    <ProductCard title="Producto A">
      <template v-slot:footer>
        <button @click="purchaseProduct">Comprar</button>
      </template>
    </ProductCard>
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue'

export default {
  components: {
    ProductCard
  },
  methods: {
    purchaseProduct() {
      alert('Producto comprado!')
    }
  }
}
</script>
```

**Componente Hijo (ProductCard.vue):**

```vue
<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <slot></slot>
    <slot name="footer"></slot>
  </div>
</template>

<script>
export default {
  props: ['title']
}
</script>

<style scoped>
.card {
  border: 1px solid #ccc;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
</style>
```

#### **Explicación:**

- **Props y Slots**: El componente `ProductCard` recibe un prop `title` y permite contenido dinámico con `slot`.
- **Reutilización**: Este patrón de componentes permite crear múltiples tarjetas de productos con contenido y estilos consistentes.

---

### 6. **Props y $emit**

#### **Concepto:**

- **Props**: Son la forma en que los componentes padres pasan datos a los componentes hijos.
- **$emit**: Permite a un componente hijo enviar eventos de vuelta al componente padre, facilitando la comunicación bidireccional.

#### \*\*Ejemplo Completo

### 6. **Props y $emit**

#### **Concepto:**

- **Props**: Los props son la forma en que un componente padre pasa datos a un componente hijo. Estos se declaran en el componente hijo y se vinculan en el componente padre.
- $emit` se utiliza para que un componente hijo envíe eventos al componente padre, permitiendo la comunicación bidireccional. Es especialmente útil cuando se quiere notificar al componente padre sobre alguna acción que ocurrió en el hijo, como el clic de un botón.

#### **Ejemplo Completo:**

**Componente Padre :**

```vue
<template>
  <div>
    <h2>Lista de Tareas</h2>
    <TaskForm @add-task="addTask" />
    <TaskList :tasks="tasks" @remove-task="removeTask" />
  </div>
</template>

<script>
import TaskForm from './TaskForm.vue'
import TaskList from './TaskList.vue'

export default {
  components: {
    TaskForm,
    TaskList
  },
  data() {
    return {
      tasks: [
        { id: 1, title: 'Estudiar Vue.js' },
        { id: 2, title: 'Desarrollar una aplicación' }
      ]
    }
  },
  methods: {
    addTask(newTask) {
      this.tasks.push(newTask)
    },
    removeTask(id) {
      this.tasks = this.tasks.filter((task) => task.id !== id)
    }
  }
}
</script>
```

**Componente Hijo 1 (TaskForm.vue):**

```vue
<template>
  <div>
    <input v-model="newTaskTitle" placeholder="Nueva tarea" />
    <button @click="submitTask">Agregar Tarea</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTaskTitle: ''
    }
  },
  methods: {
    submitTask() {
      if (this.newTaskTitle) {
        this.$emit('add-task', { id: Date.now(), title: this.newTaskTitle })
        this.newTaskTitle = ''
      }
    }
  }
}
</script>
```

**Componente Hijo 2 (TaskList.vue):**

```vue
<template>
  <ul>
    <li v-for="task in tasks" :key="task.id">
      {{ task.title }}
      <button @click="$emit('remove-task', task.id)">Eliminar</button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    tasks: Array
  }
}
</script>
```

#### **Explicación:**

- **Props**: En el componente `TaskList.vue`, `tasks` es un prop que recibe un array de tareas del componente padre. Esto permite que `TaskList.vue` muestre la lista de tareas.
- **$emit**: En `TaskForm.vue`, se usa `$emit` para enviar un evento `add-task` al componente padre cuando se agrega una nueva tarea. En `TaskList.vue`, se utiliza `$emit` para enviar un evento `remove-task` al padre cuando se elimina una tarea.

#### **Ejemplo de Uso Cotidiano:**

Imagina una aplicación de carrito de compras donde los productos en el carrito son gestionados por un componente padre. El componente hijo que muestra el carrito puede usar props para mostrar los productos y `$emit` para notificar al padre cuando un producto se elimina.

---

### 7. **Slots**

#### **Concepto:**

Los slots en Vue permiten a los componentes padres pasar contenido dinámico que se renderizará en el componente hijo. Es una poderosa herramienta para crear componentes reutilizables y flexibles.

#### **Ejemplo Completo:**

**Componente Padre (ParentComponent.vue):**

```vue
<template>
  <div>
    <ProductCard>
      <template v-slot:header>
        <h3>Producto Especial</h3>
      </template>
      <template v-slot:footer>
        <button @click="purchaseProduct">Comprar</button>
      </template>
    </ProductCard>
  </div>
</template>

<script>
import ProductCard from './ProductCard.vue'

export default {
  components: {
    ProductCard
  },
  methods: {
    purchaseProduct() {
      alert('Producto comprado!')
    }
  }
}
</script>
```

**Componente Hijo (ProductCard.vue):**

```vue
<template>
  <div class="card">
    <slot name="header"></slot>
    <p>Descripción del producto aquí...</p>
    <slot name="footer"></slot>
  </div>
</template>

<script>
export default {}
</script>

<style scoped>
.card {
  border: 1px solid #ccc;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}
</style>
```

#### **Explicación:**

- **Slots**: En `ProductCard.vue`, los slots `header` y `footer` permiten que el componente padre inserte contenido personalizado en esas áreas del componente hijo.
- **Flexibilidad**: Esto es útil cuando necesitas reutilizar un componente en diferentes contextos, con diferentes contenidos en las mismas posiciones.

#### **Ejemplo de Uso Cotidiano:**

En una tienda online, podrías usar slots para permitir que los desarrolladores personalicen diferentes partes de una tarjeta de producto, como el título, la descripción, y el pie de página, mientras reutilizan el mismo componente de tarjeta.
