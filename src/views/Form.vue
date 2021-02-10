<template>
  <v-container>
    <v-layout
        text-center
        wrap
    >
      <v-flex xs3>

      </v-flex>
      <v-flex
          xs6
      >
        <form>
          <v-text-field
              v-model="id_anggaran"
              label="ID Angaran"
              required
          ></v-text-field>
          <v-text-field
              v-model="id_opd"
              label="ID OPD"
              required
          ></v-text-field>
          <v-text-field
              v-model="jns_instansi"
              label="Jenis Instansi"
              required
          ></v-text-field>
          <v-text-field
              v-model="kd_urusan"
              label="KD Urusan"
          ></v-text-field>
          <v-text-field
              v-model="kd_bidurusan"
              label="KD Bidang Urusan"
          ></v-text-field>
          <v-text-field
              v-model="kd_program"
              label="KD Program"
          ></v-text-field>
          <v-text-field
              v-model="kd_kegiatan"
              label="KD Kegiatan"
          ></v-text-field>
          <v-text-field
              v-model="kd_subkegiatan"
              label="KD Sub Kegiatan"
          ></v-text-field>
          <v-text-field
              v-model="id_fungsi"
              label="ID Fungsi"
          ></v-text-field>
          <v-text-field
              v-model="uraian"
              label="Uraian"
          ></v-text-field>
          <v-text-field
              v-model="hd_anggaran"
              label="HD Anggaran"
          ></v-text-field>
          <v-text-field
              v-model="clevel"
              label="Clevel"
          ></v-text-field>
          <v-text-field
              v-model="hd"
              label="HD"
          ></v-text-field>
          <v-text-field
              v-model="id_rencana"
              label="ID Rencana"
          ></v-text-field>
          <v-text-field
              v-model="nilai"
              label="Nilai"
              type="number"
          ></v-text-field>
          <v-text-field
              v-model="nilai_ubah"
              label="Nilai Ubah"
              type="number"
          ></v-text-field>
          <v-text-field
              v-model="realisasi"
              label="Realisasi"
              type="number"
          ></v-text-field>
          <v-text-field
              v-model="tu_capai"
              label="TU Capai"
          ></v-text-field>
          <v-text-field
              v-model="tk_capai"
              label="TK Capai"
          ></v-text-field>


          <v-btn class="mr-4" @click="submit">submit</v-btn>
          <v-btn @click="clear">clear</v-btn>
        </form>

      </v-flex>
      <v-flex xs3>

      </v-flex>
      <div class="text-center ma-2">
        <v-snackbar
            v-model="snackbar"
        >
          {{ snackbarText }}
          <v-btn
              color="pink"
              text
              @click="snackbar = false"
          >
            Close
          </v-btn>
        </v-snackbar>
      </div>
    </v-layout>
  </v-container>
</template>

<script>

export default {
  data: () => ({
    id_anggaran: "",
    id_opd: "",
    jns_instansi: "",
    kd_urusan: "",
    kd_bidurusan:"",
    kd_program: "",
    kd_kegiatan: "",
    kd_subkegiatan: "",
    id_fungsi: "",
    uraian: "",
    hd_anggaran: "",
    clevel: "",
    hd: "",
    id_rencana: "",
    nilai: "0",
    nilai_ubah: "0",
    realisasi: "0",
    tu_capai: "",
    tk_capai: "",
    snackbar:false,
    snackbarText:""
  }),
  mounted() {
  },
  methods: {
    submit () {
      let postData = {
        id_anggaran: this.id_anggaran,
        id_opd: this.id_opd,
        jns_instansi: this.jns_instansi,
        kd_urusan: this.kd_urusan,
        kd_bidurusan:this.kd_bidurusan,
        kd_program: this.kd_program,
        kd_kegiatan: this.kd_kegiatan,
        kd_subkegiatan: this.kd_subkegiatan,
        id_fungsi: this.id_fungsi,
        uraian: this.uraian,
        hd_anggaran: this.hd_anggaran,
        clevel: this.clevel,
        hd: this.hd,
        id_rencana: this.id_rencana,
        nilai: parseInt(this.nilai),
        nilai_ubah: parseInt(this.nilai_ubah),
        realisasi: parseInt(this.realisasi),
        tu_capai: this.tu_capai,
        tk_capai: this.tk_capai
      }
      this.$http.post(process.env.VUE_APP_ALICE,postData)
          .then(response => {
            this.snackbarText=response.data.message
            this.snackbar=true
            this.clear()
          })
          .catch(response => {
            this.snackbarText=response.data.message
            this.snackbar=true
          })
    },
    clear () {
      this.id_anggaran= ""
      this.id_opd= ""
      this.jns_instansi= ""
      this.kd_urusan= ""
      this.kd_bidurusan=""
      this.kd_program= ""
      this.kd_kegiatan= ""
      this.kd_subkegiatan= ""
      this.id_fungsi= ""
      this.uraian= ""
      this.hd_anggaran= ""
      this.clevel= ""
      this.hd= ""
      this.id_rencana= ""
      this.nilai= ""
      this.nilai_ubah= ""
      this.realisasi= ""
      this.tu_capai= ""
      this.tk_capai= ""
    },
  }
};
</script>