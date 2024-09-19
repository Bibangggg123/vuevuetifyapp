<template>
  <v-container
    fluid
    class="d-flex align-center justify-center fill-height"
    style="
      background-image: url('https://static.vecteezy.com/system/resources/previews/023/516/502/non_2x/cat-seamless-pattern-calico-halloween-kitten-tile-background-scarf-isolated-wallpaper-vector.jpg');
      background-size: cover;
      background-position: center;
      background-repeat: no-repeat;
    "
  >
    <v-card max-width="500" class="pa-10" style="width: 400px; background-color: rgba(255, 255, 255, 0.8);">
      <!-- Added a transparent white background to the card for better readability -->
      <v-card-title class="text-center">
        <h2 class="text-h5" style="font-weight: bold; color: #d5006d;">My Todo List</h2>
        <!-- Changed the font weight to bold and applied dark pink color -->
      </v-card-title>
      <v-card-text>
        <v-text-field
          v-model="newTask"
          label="Add a new task"
          @keyup.enter="addTask"
          outlined
          clearable
          class="mb-4"
          style="font-size: 20px;"
        ></v-text-field>
        <v-list>
          <v-list-item
            v-for="(task, index) in tasks"
            :key="index"
            :class="{ completed: task.completed }"
            @click="toggleTask(index)"
          >
            <v-list-item-content>
              <v-list-item-title>
                <span
                  :class="{ 'text-pink': task.completed }"
                  style="font-size: 22px; font-weight: bold; color: #d5006d;">
                  <!-- Bold and dark pink color -->
                  {{ task.text }}
                </span>
              </v-list-item-title>
            </v-list-item-content>
            <v-list-item-action>
              <v-btn icon @click.stop="removeTask(index)">
                <v-icon>mdi-delete</v-icon>
              </v-btn>
            </v-list-item-action>
          </v-list-item>
        </v-list>
      </v-card-text>
    </v-card>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      newTask: '', // For input field model
      tasks: [], // Task list array
    };
  },
  methods: {
    addTask() {
      // Add new task if not empty
      if (this.newTask.trim()) {
        this.tasks.push({ text: this.newTask, completed: false });
        this.newTask = ''; // Clear input field after adding
      }
    },
    removeTask(index) {
      // Remove task by index
      this.tasks.splice(index, 1);
    },
    toggleTask(index) {
      // Toggle task completion status
      this.tasks[index].completed = !this.tasks[index].completed;
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
  color: #9e9e9e; /* Light gray for completed tasks */
}
.text-pink {
  color: #d5006d; /* Dark pink for task text */
}
</style>
