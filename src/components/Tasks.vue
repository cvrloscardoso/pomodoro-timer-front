<template>
  <div class="container-fluid">
    <div class="alert alert-warning" role="alert" v-show="tasks.length === 0">
      Não existem tarefas!
    </div>
    <table class="table table-striped" v-show="tasks.length > 0">
      <thead>
        <tr>
          <th>Id</th>
          <th>Tarefa</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" v-bind:key="task.id">
          <td>{{ task.id }}</td>
          <td>{{ task.task_name }}</td>
          <td>
            <button v-show="!task.id == ''" class="btn btn-danger" v-on:click="finish_task(index)">
              Finalizar
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <div class="form-group">
      <p>
        <input placeholder="Id da tarefa" type="text"
          name="taskId"
          class="form-control"
          v-model="id"
        >
      </p>
      <p>
        <input placeholder="Nome da tarefa" type="text"
          name="taskName"
          class="form-control"
          v-model="task_name"
        >
      </p>
      <button class="btn btn-primary" v-on:click="add_task()">
        Adicionar
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tasks',
  props: {
    msg: String
  },
  data() {
    return {
      tasks: [{

        },
      ],
      id: '',
      task_name: '',
    }
  },
  methods: {
    finish_task(task_id) {
      this.tasks.splice(task_id, 1);
    },
    add_task() {
      this.tasks.push({
        id: this.id,
        task_name: this.task_name,
      });

      this.id = '';
      this.task_name = '';
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.container-fluid {
  max-width: 50%;
}

h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
