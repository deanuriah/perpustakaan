<template>
  <div>
    <div class="col-md-6 m-auto p-3">
      <h1 class="text-center"><center>Isi Data Pengunjung Perpus</center></h1>
      <form @submit.prevent="simpan()">
        <input
        v-model="nama" 
        placeholder="nama" 
        >
        <br/>
        <input 
        v-model="kelas" 
        placeholder="kelas" 
        />
        <br/>
        <input 
        v-model="jurusan" 
        placeholder="jurusan" 
        />
        <br/>
        <input 
        v-model="keperluan" 
        placeholder="keperluan" 
        />
        <br/>
        <button type="submit">Kirim</button>
        <NuxtLink to="/pengunjung/siswa">Kembali</NuxtLink>
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
