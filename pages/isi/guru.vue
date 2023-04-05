<template>
  <div>
    <div class="col-md-6 m-auto p-3">
      <h1 class="container"><center>Isi Data Pengunjung Perpus</center></h1>
      <form @submit.prevent="simpan()">
        <input v-model="nama" placeholder="nama" class="input w-full max-w-xs" />
        <br />
        <input v-model="jabatan" placeholder="jabatan" class="input w-full max-w-xs" />
        <br />
        <input v-model="keperluan" placeholder="keperluan" class="input w-full max-w-xs" />
        <br />
        <button type="submit" class="btn btn-info text-white me-3">Kirim</button>
        <NuxtLink to="/pengunjung/guru" class="btn btn-dark text-decoraton-none text-light">Kembali</NuxtLink>
      </form>
    </div>
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
