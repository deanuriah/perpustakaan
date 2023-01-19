<template>
  <div>
    <h1>Isi Data Pengunjung Perpus</h1>
    <form @submit.prevent="simpan()">
      <input v-model="nama" placeholder="nama" />
      <input v-model="kelas" placeholder="kelas" />
      <input v-model="jurusan" placeholder="jurusan" />
      <input v-model="keperluan" placeholder="keperluan" />
      <button type="submit">Kirim</button>
      <NuxtLink to="/pengunjung/siswa">Kembali</NuxtLink>
    </form>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const nama = ref();
const kelas = ref();
const jurusan = ref();
const keperluan = ref();
async function simpan() {
  await supabase.from("pengunjungsiswa").insert({
    nama: nama.value,
    kelas: kelas.value,
    jurusan: jurusan.value,
    keperluan: keperluan.value,
  });
  const router = useRouter();
  router.push("/pengunjung/siswa");
}
</script>