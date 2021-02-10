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
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="number"
              label="Number"
              type="number"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
          ></v-text-field>
          <v-text-field
              v-model="name"
              label="Name"
              required
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
    nilai: "",
    nilai_ubah: "",
    realisasi: "",
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
      this.$http.post(process.env.VUE_APP_ALICE + "/create",postData)
          .then(response => {
            this.snackbarText=response.data.message
            this.snackbar=true
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