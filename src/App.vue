<template>
  <main class= "columns is-gapless is-multiline">
    <div class="column is-one-quarter">
      <MenuLateral />
    </div>
    <div class ="column is-three-quarter">
      <FormularioAlura/>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import MenuLateral from './components/MenuLateral.vue'
import FormularioAlura from './components/Formulario.vue'

export default defineComponent({
  name: 'App',
  components: {
    MenuLateral,
    FormularioAlura
  }
});
</script>

<style>

</style>
