<script>
import LanguageSwitcher from "./public/components/language-switcher.component.vue";

export default {
  name: 'app',
  components: { LanguageSwitcher },
  title: 'SaboresCercanos',
  data() {
    return {
      drawer: false, // Puedes cambiar esto a false para que el drawer no aparezca
      items: [
        { label: 'Cocineros', to: '/chefs' },
        { label: 'Recetas', to: '/recipes' },
        { label: 'Platos', to: '/dishes'},
        { label: 'Nutrientes', to: '/nutrients' },
        { label: 'Ordenes', to: '/orders' }
      ]
    }
  },
  methods: {
    toggleDrawer() {
      this.drawer = !this.drawer;
    }
  }
}
</script>

<template>
  <pv-toast/>
  <pv-confirm-dialog/>
  <header>
    <pv-toolbar class="dark-toolbar full-width">
      <template #start>
        <img src="/src/assets/Logo_Sabores_Cercano.png" alt="Logo" width="80px" />
        <h3 class="title-color">Sabores Cercanos</h3>
      </template>
      <template #center>
        <div class="flex-column">
          <router-link v-for="item in items"
                       :key="item.label"
                       v-slot="{ navigate, href }"
                       :to="item.to" custom>
            <pv-button class="p-button-text no-border" :href="href" @click="navigate">{{item.label}}</pv-button>
          </router-link>
        </div>
      </template>
    </pv-toolbar>
  </header>
  <main>
    <router-view/>
  </main>
</template>

<style scoped>
/* Estilo para que el toolbar ocupe todo el ancho */
.full-width {
  width: 100%; /* Hace que el toolbar sea del ancho completo */
  position: fixed; /* Fija el toolbar en la parte superior */
  top: 0;
  left: 0;
  height: 80px;
  z-index: 1000; /* Asegura que se superponga al contenido */
}

/* Estilo para el toolbar */
.dark-toolbar {
  background-color: #f5deb3; /* Cambia el color de fondo a naranja */
  color: white; /* Texto en color blanco */
  display: flex;
  align-items: center;
  align-content: center;
}

/* Estilo para los botones del toolbar sin borde */
.no-border {
  border: none; /* Elimina el borde de los botones */
  background: none; /* Elimina el fondo del botón */
  color: white; /* Asegura que el texto sea blanco */
}

/* Oculta el pv-drawer */
pv-drawer {
  display: none; /* Oculta completamente el drawer */
}

</style>
