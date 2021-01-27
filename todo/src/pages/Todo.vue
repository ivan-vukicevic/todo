<template>
  <q-page class="bg-grey-3 column">
    <q-list class="bg-white">
      <q-item
        clickable
        v-for="task in tasks"
        :key="task.title"
        :class="{ 'done bg-blue-10': task.done }"
        @click="task.done = !task.done"
        v-ripple
      >
        <q-item-section avatar>
          <q-checkbox
            color="primary"
            v-model="task.done"
            class="no-pointer-events"
          />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
      </q-item>
    </q-list>

    
  </q-page>
</template>

<script>
export default {
  data() {
    return {
      tasks: [
        {
          title: "Napravi novi sajt",
          done: false
        },
        {
          title: "Skuvaj surimi",
          done: false
        },
        {
          title: "Pogledaj anime",
          done: false
        }
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
.done {
  .q-item__label {
    text-decoration: line-through;
    color: #bbb;
  }
}
</style>
