<template>
  <div>
    <h1>Data Pengunjung Perpus</h1>
    <NuxtLink to="/isi/siswa">Isi siswa</NuxtLink>
    <NuxtLink to="/isi/guru">Isi guru</NuxtLink>
    <table border="1" width="50%">
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