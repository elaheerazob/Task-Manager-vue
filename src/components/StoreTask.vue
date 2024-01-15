<script setup>
import { ref} from 'vue';

const tasks = ref( [
    {
        name:"Task -1",
        time: '60 min'
    },
    {
        name:"Task -2",
        time: '60 min'
    },
    {
        name:"Task -3",
        time: '60 min'
    }
])

const newTaskName = ref('')
const newTaskTime = ref('')

function remove (index){
    tasks.value.splice(index, 1);
}


function addTask() {
  const newTask = {
    name: newTaskName.value,
    time: newTaskTime.value
  };
  tasks.value.push(newTask);
  // Clear input fields after adding task
  newTaskName.value = '';
  newTaskTime.value = '';
}

const toggleFrom = ref(false)

</script>
<template>
<div>
  <div class="text-center">
  <h2 class="mb-5">This is Task Manager</h2>
  <button @click="toggleFrom = !toggleFrom" type="button" class="text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 ">This is Task Manager</button>
  </div>

<!-- add to task form-->
<form v-if="toggleFrom"  class="max-w-sm mx-auto" action="">
  <div class="mr-5 flex flex-row ">
    <div class="mr-5 text-center">
    <label  class="block mb-2 text-sm font-medium text-gray-900 ">Task Name</label>
    <input v-model="newTaskName" type="text" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 " placeholder="Enter Task Name" >
    </div>
    <div class="text-center">
    <label  class="block mb-2 text-sm font-medium text-gray-900 ">Task Time</label>
    <input v-model="newTaskTime" type="number" class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 " placeholder="Enter Task Time" >
    </div>
    
  </div>
  <div class="text-center mt-5">
    <button @click="addTask()" type="button" class="text-center text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 ">Add Task</button>
  </div>
</form>

<!-- Form end -->


<div class="w-96 mx-auto max-w-md p-4 mt-10 bg-white border border-gray-200 rounded-lg shadow sm:p-8 ">
<div v-for="(task,index) in tasks" :key="index" class="flow-root">
        <ul role="list" class="divide-y divide-gray-200 ">
            <li class="py-3 sm:py-4">
              <div class="flex justify-between">
                <div class="flex items-center">
                    <div class="flex-shrink-0">
                       <p class="mr-5">{{index}}</p>
                    </div>
                    <div class="flex flex-row ">
                        <p class="text-sm font-medium text-gray-900 truncate ">
                           {{ task.name }}
                        </p>
                        <p class=" ml-5 text-sm font-medium text-gray-900 truncate ">
                            {{ task.time }}
                        </p>
                    </div>
                </div>
                 <div @click="remove(index)" class="inline-flex items-center text-base font-semibold text-gray-900 ">
                      <button type="button" class="focus:outline-none text-white bg-red-700 hover:bg-red-800 focus:ring-4 focus:ring-red-300 font-medium rounded-lg text-sm px-5 py-2.5 me-2 mb-2 ">Delete</button>
                    </div>
              </div>
            </li>
        </ul>
</div>
</div>
</div>


    <!-- <div>
        <h2 class="text-2xl ">Task Manager</h2>
    </div>

    <div>
    <h3>Add New Task</h3>
    <label for="taskName">Task Name:</label>
    <input v-model="newTaskName" type="text" id="taskName" />
    <label for="taskTime">Task Time:</label>
    <input v-model="newTaskTime" type="text" id="taskTime" />
    <button @click="addTask()">Add Task</button>
  </div> -->


    <!-- <div v-for="(task,index) in tasks" :key="index" class="flex">
        <p class="pl-5">{{ index }}</p>
        <p>{{ task.name }}</p>
        <p>{{ task.time }}</p>
        <button @click="remove(index)" >Det</button>
    </div> -->

</template>


<style scoped>

</style>