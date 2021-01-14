<template>
    <div class="tarefas">
        <H3>{{titulo}}</H3>
        <div id="lista">
            <ul v-if="tarefas">
                <li v-for="tarefa in tarefas" :key="tarefa.id">
                    {{tarefa.nome}} - 
                    <span v-if="tarefa.concluida">Concluída</span>
                    <span v-else>A Concluir</span>
                </li>
            </ul>
            <div v-else><p>Não há tarefas</p></div>
        </div>
        <button type="button" @click="criarTarefa">Criar Tarefa</button>
    </div>
</template>
<script>
import { dadosTarefas } from '../servico/tarefas';
export default {
    name: 'Tarefas',
    data() {
        return {
            titulo: 'Lista de Tarefas',
            tarefas: [],
        }
    },
    created() {
        this.obterTarefas();
    },
    methods: {
        criarTarefa() {
            this.$router.push('/criarTarefa')
        },
        obterTarefas() {
            this.tarefas = dadosTarefas.getTarefas();
        },
    },
}
</script>
<style scoped>
.tarefas {
    text-align: left;
    font-size: 12px;
    margin-left: 30px;
}
#lista {
    text-align: left;
}
</style>