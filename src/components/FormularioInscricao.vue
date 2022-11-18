<template>
    <div class="box formulario">
        <div class="columns">
            <div  class="column is-8" role="form" aria-label="Formulario para criação de uma nova tarefa">
                <input type="text" class="input" 
                placeholder="Qual tarefa deseja iniciar?"
                v-model="descricao"
                > 
            </div>
            <div class="column">
                <Temporizador @aoTemporizadorFinalizado="finalizarTarefa" />
              
            </div>
        </div>
    </div>
</template>

<script lang="ts">

import { defineComponent } from 'vue';
import Temporizador from './Temporizador.vue';

export default defineComponent({
    name: "FormularioInscricao",
    emits:['aoSalvarTarefa'],
    components: { Temporizador },
    data (){
      return{
        descricao: ''
      }
    },
    methods:{
        finalizarTarefa(tempoDecorrido: number): void{
         //   console.log('tempo da tarefa ', tempoDecorrido);
          //  console.log('descricao da tarefa', this.descricao);
          this.$emit('aoSalvarTarefa', {
            duracaoEmSegundos: tempoDecorrido,
            descricao: this.descricao
          })
            this.descricao = ''
        }
    }
})
</script>

<style>
.nav-wrapper  {
 
    background-color: #a5d6a7  !important;
 
    font-size: 14px;
 
  }

  .formulario {
    color: var(--texto-primario);
    background-color: var(--bg-primario);
  }
</style>