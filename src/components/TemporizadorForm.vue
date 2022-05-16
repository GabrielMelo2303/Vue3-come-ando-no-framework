<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <CronometroForm :tempoEmSegundos="tempoEmSegundos"/>
    <button class="button" @click="iniciar" :disabled="cronometroRodando">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!cronometroRodando">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import CronometroForm from './CronometroForm.vue'

export default defineComponent({
  name: "TemporizadorForm", // onde declaro meu componente
  components: { // aqui é onde trazemos algum componente para utilizar em outro componente
    CronometroForm
  },
  emits: ['aoTemporizadorFinalizado'], // o Emits é a lista de evento que o componente pode emitir.
  data (){ // Data é responsável pelos estados dos componentes.
    return{
      tempoEmSegundos: 0,
      cronometro: 0,
      cronometroRodando:false,
    }
  },
  methods:{ // methods é responsável pelos Metodos dos componentes
    iniciar(){
      //Começar a contar
      // 1seg = 1000 ms
      this.cronometroRodando = true
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos ++
      }, 1000)
    },
    finalizar(){
      this.cronometroRodando = false
      clearInterval(this.cronometro)
      this.$emit('aoTemporizadorFinalizado', this.tempoEmSegundos) // este método recebe 2 parametros, o primeiro é sobre o evento que ele esta emitindo, o segundo é o payload que quem esta ouvindo o evento irá receber. 
      this.tempoEmSegundos = 0
    },
  }
});
</script>