<template>
  <AppDrop
    @drop="moveTaskOrColumn"
  >
    <AppDrag
      class="task"
      :transfer-data="{
        type: 'task',
        fromColumnIndex: columnIndex,
        fromTaskIndex: taskIndex
      }"
      @click="goToTask(task)"
    >
      <span class="w-100 flex-shrink-0 bold">
        {{ task.name }}
      </span>
      <p
        v-if="task.description"
        class="w-100 flex-shrink-0 mt-1 small"
      >
        {{ task.description }}
      </p>
    </AppDrag>
  </AppDrop>
</template>

<script>
    import AppDrag from './AppDrag';
    import AppDrop from './AppDrop';
    import taskMixins from '@/plugins/taskMixins';

    export default {
  components: { AppDrag, AppDrop },
  mixins: [taskMixins],
  props: {
    task: {
      type: Object,
      required: true
    },
    taskIndex: {
      type: Number,
      required: true
    }
  },
  methods: {
    goToTask (task) {
      this.$router.push({ name: 'task', params: { id: task.id } });
    }
  }
};
</script>
