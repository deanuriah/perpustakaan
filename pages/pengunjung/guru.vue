<template>
  <div class="container">
    <h2 class="text-center"><center>Data Pengunjung Perpus</center></h2>
    <NuxtLink to="/isi/siswa" class="btn btn-primary text-decoration-none nb-3">Isi siswa</NuxtLink> <br />
    <NuxtLink to="/isi/guru"  class="btn btn-primary text-decoration-none nb-3">Isi guru</NuxtLink> <br />
    <table border="1" width="100%" class="table bg-dark text-light">
      <thead>
        <tr>
          <th>#</th>
          <th>tanggal</th>
          <th>nama</th>
          <th>jabatan</th>
          <th>keperluan</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="visitor in datas" :key="visitor.id">
          <td>{{ visitor.id }}</td>
          <td>{{ visitor.tanggal }}</td>
          <td>{{ visitor.nama }}</td>
          <td>{{ visitor.jabatan }}</td>
          <td>{{ visitor.keperluan }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const datas = ref([]);
async function getData() {
  const { data, error } = await supabase.from("pengunjungguru").select();
  datas.value = data;
}
onMounted(() => {
  getData();
});
</script>  

<style scoped>
thead {
  background-color: rgb(128, 125, 122);
}
tbody {
  background-color: rgb(231, 231, 231);
}
</style>