<template>
    <div class="p-2 px-3 border shadow-sm mt-3" :class="{checked: todo.checked}">
        <article class="d-flex align-items-center justify-content-between">
          <div class="me-3 text-start d-flex align-items-center">
            <i class="bi me-2 fs-5" :class="todo.checked ? 'bi-check-lg' : 'bi-clock'"></i>
            <span>{{ todo.description }}</span>
          </div>

          <div class="text-decoration-none text-nowrap">
            <span class="btn btn-outline-primary me-2" @click="$emit('toggle', todo)">
                <span v-if="todo.checked">Concluído</span>
                <span v-else>Desmarcar</span>
            </span>
            <span class="btn btn-outline-danger" @click="$emit('remove', todo)">Remover</span>
          </div>
        </article>
      </div>
</template>

<script>
export default {
    props: { 
        todo: { type: Object, required: true }
    }
}
</script>

<style scoped>
    .checked {
        text-decoration: line-through;
        color: lightgray;
    }
</style>
