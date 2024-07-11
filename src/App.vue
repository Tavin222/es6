<script setup>
  import { reactive } from "vue";
  import Cabeçalho from "./components/Cabeçalho.vue";
  import Formu from "./components/Formu.vue";
  import Lista from "./components/Lista.vue";
  
  const estado = reactive ({
    filtro: 'todas',
    tarefaTemp: '',
    tarefas: [
      {
        titulo: 'Estudar ES6',
        finalizada: false,
      },
      {
        titulo: 'Estudar SASS',
        finalizada: false,
      },
      {
        titulo: 'Ir para a academia',
        finalizada: true,
      }
    ]
  })

  const getTarefasPendentes = () => {
    return estado.tarefas.filter(tarefa => !tarefa.finalizada)
  }

  const getTarefasFinalizadas = () => {
    return estado.tarefas.filter(tarefa => tarefa.finalizada)
  }

  const getTarefasFiltradas = () => {
    const {filtro} = estado;

    switch(filtro) {
      case 'pendentes':
      return getTarefasPendentes();

      case 'finalizadas': 
      return getTarefasFinalizadas();

      default:
        return estado.tarefas;
    }
  }

  const cadastrarTarefa = () => {
    const tarefaNova = {
      titulo: estado.tarefaTemp,
      finalizada: false,
    }

    estado.tarefas.push(tarefaNova);
    estado.tarefaTemp = ''
  }

</script>

<template>
<div class="container">

  <Cabeçalho :tarefas-pendentes="getTarefasPendentes().length"/>
  <Formu :trocar-filtro="evento => estado.filtro = evento.target.value" :tarefa-temp="estado.tarefaTemp" :edita-tarefa-temp="evento => estado.tarefaTemp = evento.target.value" :cadastrar-tarefa="cadastrarTarefa" />
  <Lista :tarefas="getTarefasFiltradas()" />

</div>
</template>


