<template>
  <div>
    <h2>Formulir Kontak</h2>
    <form @submit.prevent="submitForm">
      <label for="nama">Nama:</label>
      <input class="{'is-Invalid':isInvalidnama}" 
      type="text" id="nama" v-model="kontak.nama"> <br>
      <div v-if="isInvalidnama" class="error-massage">nama harus di isi</div>

      <label for="email">Email:</label>
      <input class="{'is-Invalid':isInvalidemail}"
      type="email" id="email" v-model="kontak.email" required> <br>
      <div v-if="isInvalidemail" class="error-massage">email harus di isi</div>

      <button type="submit">Kirim</button>
    </form>
  </div>
  <div id="a"></div>
</template>

<script>
export default {
  data() {
    return {
      kontak: {
        nama: '',
        email: ''
      },
    };
  },

  computed: {
    isInvalidnama() {
      return this.kontak.nama.length <= 0;
    },
    isInvalidemail() {
      return this.kontak.email.length <= 0;
    },
  },

  methods: {
    submitForm() {
      // Lakukan sesuatu dengan data kontak
      document.getElementById('a').innerHTML = ("nama: " + this.kontak.nama) + ("<br>email: " + this.kontak.email);
    },
  },
};

</script>

<style>
.error-massage{
  color: rgb(255, 0, 0);
  margin-top: 5px;
}
.is-invalid{
  border-color: rgb(0, 0, 0);
}
</style>