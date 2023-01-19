<template>
  <div>
    <h1>Isi Data Pengunjung Perpus</h1>
    <form @submit.prevent="simpan()">
      <input v-model="nama" placeholder="nama" />
      <input v-model="jabatan" placeholder="jabatan" />
      <input v-model="keperluan" placeholder="keperluan" />
      <button type="submit">Kirim</button>
      <NuxtLink to="/pengunjung/guru">Kembali</NuxtLink>
    </form>
  </div>
</template>

<script setup>
const supabase = useSupabaseClient();
const nama = ref();
const jabatan = ref();
const keperluan = ref();
async function simpan() {
  await supabase.from("pengunjungguru").insert({
    nama: nama.value,
    jabatan: jabatan.value,
    keperluan: keperluan.value,
  });
  const router = useRouter();
  router.push("/pengunjung/guru");
}
</script>