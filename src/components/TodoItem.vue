<template>
  <div class="siimple-list-item">
    {{ todo.text }}
    &nbsp; &nbsp;
    <button @click="$emit('edit', todo.id)" class="siimple-btn siimple-btn--yellow">
        <i class="fas fa-pencil-alt"></i>
    </button>
    &nbsp; 
    <button @click="$emit('remove', todo.id)" class="siimple-btn siimple-btn--error">
      <i class="fas fa-trash"></i>
    </button>

  </div>
</template>

<script>
export default {
  props: {
    todo: {
      type: Object,
      required: true
    }
  }
};
</script>