<template>
  <div>
    <div class="col-md-6 m-auto p-3">
      <h1 class="container"><center>Isi Data Pengunjung Perpus</center></h1>
      <form @submit.prevent="simpan()">
        <input v-model="nama" placeholder="nama" class="input w-full max-w-xs mt-2" />
        <br />
        <input v-model="kelas" placeholder="kelas" class="input w-full max-w-xs mt-2" />
        <br />
        <input v-model="jurusan" placeholder="jurusan" class="input w-full max-w-xs mt-2" />
        <br />
        <input v-model="keperluan" placeholder="keperluan" class="input w-full max-w-xs mt-2" />
        <br />
        <button type="submit" class="btn btn-info text-white me-3">Kirim</button>
      <NuxtLink to="/pengunjung/siswa" class="btn btn-dark text-decoraton-none text-light">Kembali</NuxtLink>
      </form>
    </div>
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
