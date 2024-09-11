<script setup>
import { ref } from 'vue'

defineProps({
  msg: String,
})

const tableData = ref([
  { name: 'Mike Rowave', age: '24', cool_status: 'Cool'},
  { name: 'Large Marge', age: '27', cool_status: 'Not Cool'},
  { name: 'Lenny', age: '20', cool_status: 'Cool'},
  { name: 'Juan', age: '28', cool_status: 'Not Cool'},
])

// const count = ref(0)

function changeCoolStatus(row) {
  row.cool_status = row.cool_status === 'Cool' ? 'Not Cool' : 'Cool';
  console.log("Cool status changed to " + row.cool_status);
}

</script>

<template #table-caption>
  <h1>{{ msg }}</h1>

  <!-- <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
  </div> -->
  <table class="table">
    <thead>
      <tr>
        <th>Name</th>
        <th>Age</th>
        <th>Cool Status</th>
        <th>Actions</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="row in tableData" :key="row.name">
        <td>{{ row.name }}</td>
        <td>{{ row.age }}</td>
        <td>{{ row.cool_status }}</td>
        <td><button @click="changeCoolStatus(row)">Switch Cool Status</button></td>
      </tr>
    </tbody>
  </table>
  <p>
    Hello Mr Nesbitt, please rate my homework above :)
  </p>
</template>

<style scoped>
.table {
  width: 100%;
  border-collapse: collapse;
}

.table th,
.table td {
  padding: 8px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

.table th {
  background-color: #000000;
  padding: 12px; /* added padding */
}

.table tr:nth-child(even) {
  background-color: #000000;
}

.table button {
  padding: 6px 12px;
  background-color: #4CaF50;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

.table button:hover {
  background-color: #45a049;
}
</style>