<template>
  <div>
    <v-col cols="12">
      <v-text-field
        v-model="campoIput"
        label="Qual sua tarefa?"
        outlined
        clearable
        @keyup.enter="handleAddTarefa"
      ></v-text-field>
    </v-col>
    <v-list flat subheader>
      <v-list-item-group multiple active-class="">
        <div v-for="(tarefa, index) in $store.state.tarefas" :key="index">
          <tarefa :tarefa="tarefa" />
        </div>
      </v-list-item-group>
    </v-list>
  </div>
</template>

<script>
import Tarefa from "../components/Tarefa/Tarefa.vue";
export default {
  name: "Home",

  components: {
    Tarefa,
  },
  data() {
    return {
      campoIput: null,
    };
  },
  methods: {
    handleAddTarefa() {
      this.$store.commit("adicionaTarefa", this.campoIput);
      this.campoIput = null;
    },
  },
};
</script>
