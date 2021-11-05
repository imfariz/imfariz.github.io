<template>
    <div>
        <h1>Metode AHP</h1>
        <div class="d-flex">
            <!-- <h1>Input Perbandingan</h1> -->
            <table class="table mt-5 mb-5 mx-2 table-bordered border-secondary">
                <thead>
                    <tr>
                        <th>Kriteria</th>
                        <th>Perbandingan</th>
                        <th>Kriteria</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Logika</td>
                        <td>
                            <p> {{ text }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test">
                        </td>
                        <td>Bahasa Inggris</td>
                    </tr>
                    <tr>
                        <td>Logika</td>
                        <td>
                            <p> {{ text1 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test1">
                        </td>
                        <td>Komputer</td>
                    </tr>
                    <tr>
                        <td>Logika</td>
                        <td>
                            <p> {{ text2 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test2">
                        </td>
                        <td>Wawancara</td>
                    </tr>
                    <tr>
                        <td>Logika</td>
                        <td>
                            <p> {{ text3 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test3">
                        </td>
                        <td>Pengetahuan Umum</td>
                    </tr>
                    <tr>
                        <td>Bahasa Inggris</td>
                        <td>
                            <p> {{ text4 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test4">
                        </td>
                        <td>Komputer</td>
                    </tr>
                    <tr>
                        <td>Bahasa Inggris</td>
                        <td>
                            <p> {{ text5 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test5">
                        </td>
                        <td>Wawancara</td>
                    </tr>
                    <tr>
                        <td>Bahasa Inggris</td>
                        <td>
                            <p> {{ text7 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test7">
                        </td>
                        <td>Pengetahuan Umum</td>
                    </tr>
                    <tr>
                        <td>Komputer</td>
                        <td>
                            <p> {{ text6 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test6">
                        </td>
                        <td>Wawancara</td>
                    </tr>
                    <tr>
                        <td>Komputer</td>
                        <td>
                            <p> {{ text8 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test8">
                        </td>
                        <td>Pengetahuan Umum</td>
                    </tr>
                    <tr>
                        <td>Wawancara</td>
                        <td>
                            <p> {{ text9 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test9">
                        </td>
                        <td>Pengetahuan Umum</td>
                    </tr>
                </tbody>
            </table>
            <h2 class="align-self-center">(*) Menentukan Nilai Prioritas melalui Input Data dari User</h2>
        </div>

        <!-- Perhitungan AHP -->
        <div v-if="condition != false">
          <div class="d-flex">
            <div>
              <h1 class="mt-5">Matriks Perbandingan</h1>
              <table class="table table-stripped my-5 mx-2 table-bordered border-secondary">
                  <thead>
                      <tr>
                          <th>Alternatif</th>
                          <th v-for="k in kriteria" :key="k">{{ k.nama }}</th>
                      </tr>
                  </thead>
                  <tbody>
                      <tr>
                      <td>{{ kriteria[0].nama }}</td>
                      <td v-for="x in 5" :key="x">
                          <input type="text" style="border: none; text-align: center" v-model="kriteria[0].wt[x-1]">
                      </td>
                      </tr>
                      <tr>
                      <td>{{ kriteria[1].nama }}</td>
                      <td v-for="x in 5" :key="x">
                          <input type="text" style="border: none; text-align: center" v-model="kriteria[1].wt[x-1]">
                      </td>
                      </tr>
                      <tr>
                      <td>{{ kriteria[2].nama }}</td>
                      <td v-for="x in 5" :key="x">
                          <input type="text" style="border: none; text-align: center" v-model="kriteria[2].wt[x-1]">
                      </td>
                      </tr>
                      <tr>
                      <td>{{ kriteria[3].nama }}</td>
                      <td v-for="x in 5" :key="x">
                          <input type="text" style="border: none; text-align: center" v-model="kriteria[3].wt[x-1]">
                      </td>
                      </tr>
                      <tr>
                      <td>{{ kriteria[4].nama }}</td>
                      <td v-for="x in 5" :key="x">
                          <input type="text" style="border: none; text-align: center" v-model="kriteria[4].wt[x-1]">
                      </td>
                      </tr>
                      <tr v-if="condition != false">
                          <td>Total</td>
                          <td v-for="i in total" :key="i">{{ i }}</td>
                      </tr>
                  </tbody>
              </table>
            </div>
            <h3 class="align-self-center ms-4 text-start">
              (*) Matriks Perbandingan diperoleh dari Nilai Prioritas yang diinputkan oleh user
              untuk kemudian diterjemahkan sesuai dengan tabel Saaty
            </h3>
          </div>

          <section class="d-flex my-5">
            <div class="d-flex mx-5">
              <div>         
                <h1>Normalisasi</h1>
                <table class="table table-stripped table-bordered">
                    <thead>
                        <tr>
                            <th>Alternatif</th>
                            <th v-for="k in kriteria" :key="k">{{ k.nama }}</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="n in kriteria" :key="n">
                            <td v-text="n.nama"></td>
                            <td v-for="x in n.nm" :key="x">{{ x }}</td>
                        </tr>
                        <tr>
                            <td>Total</td>
                            <td v-for="i in total" :key="i">{{ i/i }}</td>
                        </tr>
                    </tbody>
                </table>
              </div>
              <div class="mx-5">
                <h1>Nilai Bobot</h1>
                <table class="table table-stripped table-bordered">
                    <thead>
                        <tr>
                            <th>Kriteria</th>
                            <th>Bobot</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="a in kriteria" :key="a">
                            <td v-text="a.nama"></td>
                            <td v-text="a.eigen"></td>
                        </tr>
                    </tbody>
                </table>
              </div>
              <div>
                <h1>Nilai Eigen Prioritas</h1>
                <table class="table table-stripped table-bordered">
                    <thead>
                        <tr>
                            <th>Kriteria</th>
                            <th>Jumlah</th>
                            <th>Bobot</th>
                            <th>&Lambda;</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr v-for="n in kriteria" :key="n">
                            <td v-text="n.nama"></td>
                            <td v-text="n.jumlah"></td>
                            <td v-text="n.eigen"></td>
                            <td v-text="n.lam"></td>
                        </tr>
                    </tbody>
                </table>
              </div>
            </div>
            <div class="ms-3 align-self-center text-start">
              <p>Dengan menggunakan Metode AHP diperoleh : </p>
              <ul>
                <li>Nilai Consistency Index (CI) = {{ ci }}</li>
                <li>Nilai Consistency Ratio (CR) = {{ cr }}</li>
              </ul>
              <p v-if="consistent == 'Sudah Konsisten'">Karena nilai tidak lebih dari 0.1, maka perhitungan data <strong>{{ consistent }}</strong></p>
              <p v-else>Karena lebih dari 0.1, maka perhitungan data <strong>consistent</strong></p>
            </div>
          </section>

          <section class="d-flex my-5 mx-5">
            <div>
              <h1>Kriteria Potensial</h1>
              <table class="table mt-5 mb-5 table-bordered">
                  <thead>
                      <tr>
                          <th>Alternatif</th>
                          <th>Prioritas</th>
                          <th>Bobot</th>
                      </tr>
                  </thead>
                  <tbody>
                      <tr v-for="(k, index) in kriteria" :key="k">
                          <td v-text="k.nama"></td>
                          <td><input type="text" style="border: none; text-align: center" v-model="kriteria[index].prioritas"></td>
                          <td v-text="k.eigen"></td>
                      </tr>
                  </tbody>
              </table>
            </div>
            <div class="ms-5 align-self-center">
              <h2>
                (*) Karena Consistency Ratio yang sudah Konsisten, maka tabel ini dapat digunakan untuk mengetahui kriteria mana yang punya bobot paling besar
                dan menjadi kriteria paling potensial.
              </h2>
            </div>
          </section>
        </div>

        <!--Perhitungan SAW  -->        
        <h1>Data Calon Mahasiswa</h1>
        <table class="table table-stripped mt-5 table-bordered border-secondary">
            <thead>
                <tr>
                    <th>Alternatif</th>
                    <th v-for="a in kriteria" :key="a">
                        {{ a.nama }}
                    </th>
                    <th>Vektor</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(x, index) in alt" :key="x">
                    <td>A{{ index +1 }}</td>
                    <td><input type="number" style="text-align: center" v-model="x.lm"></td>
                    <td><input type="number" style="text-align: center" v-model="x.bi"></td>
                    <td><input type="number" style="text-align: center" v-model="x.kp"></td>
                    <td><input type="number" style="text-align: center" v-model="x.wc"></td>
                    <td><input type="number" style="text-align: center" v-model="x.pu"></td>
                    <td v-text="x.v"></td>
                </tr>
            </tbody>
        </table>

        <button class="btn btn-primary float" @click="normalize">
            N
        </button>
    </div>
</template>

<script>
export default {
    name: 'DataModel',
    data() {
        return {
            condition: false,
            test: 9,
            text: "Prioritas",
            test1: 9,
            text1: "Prioritas",
            test2: 9,
            text2: "Prioritas",
            test3: 9,
            text3: "Prioritas",
            test4: 9,
            text4: "Prioritas",
            test5: 9,
            text5: "Prioritas",
            test6: 9,
            text6: "Prioritas",
            test7: 9,
            text7: "Prioritas",
            test8: 9,
            text8: "Prioritas",
            test9: 9,
            text9: "Prioritas",
            total: [],
            data: [
                {
                    nama: 'Somber',
                    c1 : 'Lumpur',
                    c2: 'Tawar',
                    c3: 0.4496
                },
                {
                    nama:'SPN',
                    c1: 'Pasir',
                    c2: 'Asin',
                    c3: 0.1040
                },
                {
                    nama:'Graha',
                    c1: 'Lumpur',
                    c2: 'Tawar',
                    c3: 0.2570
                },
                {
                    nama:'AURI',
                    c1: 'Pasir',
                    c2: 'Asin',
                    c3: 0.0944
                },
                {
                    nama:'Klandasan',
                    c1: 'Pasir',
                    c2: 'Asin',
                    c3: 0.0951
                },
            ],
            alt: [
                {
                    lm: 32.5,
                    bi: 35,
                    kp: 50,
                    wc: 75,
                    pu: 35,
                    v: 0
                },
                {
                    lm: 42.5,
                    bi: 30,
                    kp: 55,
                    wc: 72.9,
                    pu: 60,
                    v: 0
                },
                {
                    lm: 42.5,
                    bi: 35,
                    kp: 60,
                    wc: 83.6,
                    pu: 40,
                    v: 0
                },
                {
                    lm: 30,
                    bi: 15,
                    kp: 50,
                    wc: 81.4,
                    pu: 45,
                    v: 0
                }
            ],
            kriteria: [
                {
                    nama: 'Logika',
                    prioritas: 1,
                    wt: [1, 1, 1, 1, 1],
                    nm: [],
                    eigen: 0,
                    nEigen: [],
                    jumlah: 0,
                    lam: 0
                },
                {
                    nama: 'Bahasa Inggris',
                    prioritas: 3,
                    wt: [1, 1, 1, 1, 1],
                    nm: [],
                    eigen: 0,
                    nEigen: [],
                    jumlah: 0,
                    lam: 0
                },
                {
                    nama: 'Komputer',
                    prioritas: 2,
                    wt: [1, 1, 1, 1, 1],
                    nm: [],
                    eigen: 0,
                    nEigen: [],
                    jumlah: 0,
                    lam: 0
                },
                {
                    nama: 'Wawancara',
                    prioritas: 3,
                    wt: [1, 1, 1, 1, 1],
                    nm: [],
                    eigen: 0,
                    nEigen: [],
                    jumlah: 0,
                    lam: 0
                },
                {
                    nama: 'Pengetahuan Umum',
                    prioritas: 3,
                    wt: [1, 1, 1, 1, 1],
                    nm: [],
                    eigen: 0,
                    nEigen: [],
                    jumlah: 0,
                    lam: 0
                },
            ]
        }
    },
    computed: {
        
        eigenMax: function() {
            let em = []
            const reducer = (pr, cr) => pr + cr;
            for(let i=0; i<this.kriteria.length;i++) {
                em.push(this.kriteria[i].lam)
            }
            return em.reduce(reducer)/this.kriteria.length
        },
        ci: function() {
            return (this.eigenMax-this.kriteria.length)/(this.kriteria.length-1)
        },
        cr: function() {
            return this.ci/1.12
        },
        consistent: function() {
            return (this.cr<=0.1)? "Sudah Konsisten" : "Belum Konsisten"
        }
    },
    watch: {
      test: function(val) {
      if(val == 1) {
        this.text = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[0].wt[1] = 1/9
        this.kriteria[1].wt[0] = 9
      }
      if(val == 3 || val == 2) {
        this.text = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[0].wt[1] = 1/8
          this.kriteria[1].wt[0] = 8
        }
        if(val == 3) {
          this.kriteria[0].wt[1] = 1/7
          this.kriteria[1].wt[0] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[0].wt[1] = 1/6
          this.kriteria[1].wt[0] = 6
        }
        if(val == 5) {
          this.kriteria[0].wt[1] = 1/5
          this.kriteria[1].wt[0] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[0].wt[1] = 1/4
          this.kriteria[1].wt[0] = 4
        }
        if(val == 7) {
          this.kriteria[0].wt[1] = 1/3
          this.kriteria[1].wt[0] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[0].wt[1] = 1/2
          this.kriteria[1].wt[0] = 2
        }
        if(val == 9) {
          this.kriteria[0].wt[1] = 1
        }
        if(val == 10) {
          this.kriteria[0].wt[1] = 2
          this.kriteria[1].wt[0] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[0].wt[1] = 3
          this.kriteria[1].wt[0] = 1/3
        }
        if(val == 12) {
          this.kriteria[0].wt[1] = 4
          this.kriteria[1].wt[0] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[0].wt[1] = 5
          this.kriteria[1].wt[0] = 1/5
        }
        if(val == 14) {
          this.kriteria[0].wt[1] = 6
          this.kriteria[1].wt[0] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[0].wt[1] = 7
          this.kriteria[1].wt[0] = 1/7
        }
        if(val == 16) {
          this.kriteria[0].wt[1] = 8
          this.kriteria[1].wt[0] = 1/8
        }
      }
      if(val == 17) {
        this.text = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[0].wt[1] = 9
          this.kriteria[1].wt[0] = 1/9
        }
      } 
    },
      test1: function(val) {
      if(val == 1) {
        this.text1 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[0].wt[2] = 1/9
        this.kriteria[2].wt[0] = 9
      }
      if(val == 3 || val == 2) {
        this.text1 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[0].wt[2] = 1/8
          this.kriteria[2].wt[0] = 8
        }
        if(val == 3) {
          this.kriteria[0].wt[2] = 1/7
          this.kriteria[2].wt[0] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text1 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[0].wt[2] = 1/6
          this.kriteria[2].wt[0] = 6
        }
        if(val == 5) {
          this.kriteria[0].wt[2] = 1/5
          this.kriteria[2].wt[0] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text1 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[0].wt[2] = 1/4
          this.kriteria[2].wt[0] = 4
        }
        if(val == 7) {
          this.kriteria[0].wt[2] = 1/3
          this.kriteria[2].wt[0] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text1 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[0].wt[2] = 1/2
          this.kriteria[2].wt[0] = 2
        }
        if(val == 9) {
          this.kriteria[0].wt[2] = 1
        }
        if(val == 10) {
          this.kriteria[0].wt[2] = 2
          this.kriteria[2].wt[0] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text1 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[0].wt[2] = 3
          this.kriteria[2].wt[0] = 1/3
        }
        if(val == 12) {
          this.kriteria[0].wt[2] = 4
          this.kriteria[2].wt[0] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text1 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[0].wt[2] = 5
          this.kriteria[2].wt[0] = 1/5
        }
        if(val == 14) {
          this.kriteria[0].wt[2] = 6
          this.kriteria[2].wt[0] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text1 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[0].wt[2] = 7
          this.kriteria[2].wt[0] = 1/7
        }
        if(val == 16) {
          this.kriteria[0].wt[2] = 8
          this.kriteria[2].wt[0] = 1/8
        }
      }
      if(val == 17) {
        this.text1 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[0].wt[2] = 9
          this.kriteria[2].wt[0] = 1/9
        }
      } 
    },
      test2: function(val) {
      if(val == 1) {
        this.text2 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[0].wt[3] = 1/9
        this.kriteria[3].wt[0] = 9
      }
      if(val == 3 || val == 2) {
        this.text2 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[0].wt[3] = 1/8
          this.kriteria[3].wt[0] = 8
        }
        if(val == 3) {
          this.kriteria[0].wt[3] = 1/7
          this.kriteria[3].wt[0] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text2 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[0].wt[3] = 1/6
          this.kriteria[3].wt[0] = 6
        }
        if(val == 5) {
          this.kriteria[0].wt[3] = 1/5
          this.kriteria[3].wt[0] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text2 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[0].wt[3] = 1/4
          this.kriteria[3].wt[0] = 4
        }
        if(val == 7) {
          this.kriteria[0].wt[3] = 1/3
          this.kriteria[3].wt[0] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text2 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[0].wt[3] = 1/2
          this.kriteria[3].wt[0] = 2
        }
        if(val == 9) {
          this.kriteria[0].wt[3] = 1
        }
        if(val == 10) {
          this.kriteria[0].wt[3] = 2
          this.kriteria[3].wt[0] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text2 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[0].wt[3] = 3
          this.kriteria[3].wt[0] = 1/3
        }
        if(val == 12) {
          this.kriteria[0].wt[3] = 4
          this.kriteria[3].wt[0] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text2 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[0].wt[3] = 5
          this.kriteria[3].wt[0] = 1/5
        }
        if(val == 14) {
          this.kriteria[0].wt[3] = 6
          this.kriteria[3].wt[0] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text2 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[0].wt[3] = 7
          this.kriteria[3].wt[0] = 1/7
        }
        if(val == 16) {
          this.kriteria[0].wt[3] = 8
          this.kriteria[3].wt[0] = 1/8
        }
      }
      if(val == 17) {
        this.text2 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[0].wt[3] = 9
          this.kriteria[3].wt[0] = 1/9
        }
      } 
    },
      test3: function(val) {
      if(val == 1) {
        this.text3 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[0].wt[4] = 1/9
        this.kriteria[4].wt[0] = 9
      }
      if(val == 3 || val == 2) {
        this.text3 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[0].wt[4] = 1/8
          this.kriteria[4].wt[0] = 8
        }
        if(val == 3) {
          this.kriteria[0].wt[4] = 1/7
          this.kriteria[4].wt[0] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text3 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[0].wt[4] = 1/6
          this.kriteria[4].wt[0] = 6
        }
        if(val == 5) {
          this.kriteria[0].wt[4] = 1/5
          this.kriteria[4].wt[0] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text3 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[0].wt[4] = 1/4
          this.kriteria[4].wt[0] = 4
        }
        if(val == 7) {
          this.kriteria[0].wt[4] = 1/3
          this.kriteria[4].wt[0] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text3 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[0].wt[4] = 1/2
          this.kriteria[4].wt[0] = 2
        }
        if(val == 9) {
          this.kriteria[0].wt[4] = 1
        }
        if(val == 10) {
          this.kriteria[0].wt[4] = 2
          this.kriteria[4].wt[0] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text3 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[0].wt[4] = 3
          this.kriteria[4].wt[0] = 1/3
        }
        if(val == 12) {
          this.kriteria[0].wt[4] = 4
          this.kriteria[4].wt[0] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text3 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[0].wt[4] = 5
          this.kriteria[4].wt[0] = 1/5
        }
        if(val == 14) {
          this.kriteria[0].wt[4] = 6
          this.kriteria[4].wt[0] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text3 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[0].wt[4] = 7
          this.kriteria[4].wt[0] = 1/7
        }
        if(val == 16) {
          this.kriteria[0].wt[4] = 8
          this.kriteria[4].wt[0] = 1/8
        }
      }
      if(val == 17) {
        this.text3 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[0].wt[4] = 9
          this.kriteria[4].wt[0] = 1/9
        }
      } 
    },
      test4: function(val) {
      if(val == 1) {
        this.text4 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[1].wt[2] = 1/9
        this.kriteria[2].wt[1] = 9
      }
      if(val == 3 || val == 2) {
        this.text4 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[1].wt[2] = 1/8
          this.kriteria[2].wt[1] = 8
        }
        if(val == 3) {
          this.kriteria[1].wt[2] = 1/7
          this.kriteria[2].wt[1] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text4 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[1].wt[2] = 1/6
          this.kriteria[2].wt[1] = 6
        }
        if(val == 5) {
          this.kriteria[1].wt[2] = 1/5
          this.kriteria[2].wt[1] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text4 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[1].wt[2] = 1/4
          this.kriteria[2].wt[1] = 4
        }
        if(val == 7) {
          this.kriteria[1].wt[2] = 1/3
          this.kriteria[2].wt[1] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text4 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[1].wt[2] = 1/2
          this.kriteria[2].wt[1] = 2
        }
        if(val == 9) {
          this.kriteria[1].wt[2] = 1
        }
        if(val == 10) {
          this.kriteria[1].wt[2] = 2
          this.kriteria[2].wt[1] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text4 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[1].wt[2] = 3
          this.kriteria[2].wt[1] = 1/3
        }
        if(val == 12) {
          this.kriteria[1].wt[2] = 4
          this.kriteria[2].wt[1] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text4 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[1].wt[2] = 5
          this.kriteria[2].wt[1] = 1/5
        }
        if(val == 14) {
          this.kriteria[1].wt[2] = 6
          this.kriteria[2].wt[1] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text4 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[1].wt[2] = 7
          this.kriteria[2].wt[1] = 1/7
        }
        if(val == 16) {
          this.kriteria[1].wt[2] = 8
          this.kriteria[2].wt[1] = 1/8
        }
      }
      if(val == 17) {
        this.text4 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[1].wt[2] = 9
          this.kriteria[2].wt[1] = 1/9
        }
      } 
    },
      test5: function(val) {
      if(val == 1) {
        this.text5 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[1].wt[3] = 1/9
        this.kriteria[3].wt[1] = 9
      }
      if(val == 3 || val == 2) {
        this.text5 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[1].wt[3] = 1/8
          this.kriteria[3].wt[1] = 8
        }
        if(val == 3) {
          this.kriteria[1].wt[3] = 1/7
          this.kriteria[3].wt[1] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text5 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[1].wt[3] = 1/6
          this.kriteria[3].wt[1] = 6
        }
        if(val == 5) {
          this.kriteria[1].wt[3] = 1/5
          this.kriteria[3].wt[1] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text5 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[1].wt[3] = 1/4
          this.kriteria[3].wt[1] = 4
        }
        if(val == 7) {
          this.kriteria[1].wt[3] = 1/3
          this.kriteria[3].wt[1] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text5 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[1].wt[3] = 1/2
          this.kriteria[3].wt[1] = 2
        }
        if(val == 9) {
          this.kriteria[1].wt[3] = 1
        }
        if(val == 10) {
          this.kriteria[1].wt[3] = 2
          this.kriteria[3].wt[1] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text5 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[1].wt[3] = 3
          this.kriteria[3].wt[1] = 1/3
        }
        if(val == 12) {
          this.kriteria[1].wt[3] = 4
          this.kriteria[3].wt[1] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text5 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[1].wt[3] = 5
          this.kriteria[3].wt[1] = 1/5
        }
        if(val == 14) {
          this.kriteria[1].wt[3] = 6
          this.kriteria[3].wt[1] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text5 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[1].wt[3] = 7
          this.kriteria[3].wt[1] = 1/7
        }
        if(val == 16) {
          this.kriteria[1].wt[3] = 8
          this.kriteria[3].wt[1] = 1/8
        }
      }
      if(val == 17) {
        this.text5 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[1].wt[3] = 9
          this.kriteria[3].wt[1] = 1/9
        }
      } 
    },
      test6: function(val) {
      if(val == 1) {
        this.text6 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[2].wt[3] = 1/9
        this.kriteria[3].wt[2] = 9
      }
      if(val == 3 || val == 2) {
        this.text6 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[2].wt[3] = 1/8
          this.kriteria[3].wt[2] = 8
        }
        if(val == 3) {
          this.kriteria[2].wt[3] = 1/7
          this.kriteria[3].wt[2] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text6 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[2].wt[3] = 1/6
          this.kriteria[3].wt[2] = 6
        }
        if(val == 5) {
          this.kriteria[2].wt[3] = 1/5
          this.kriteria[3].wt[2] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text6 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[2].wt[3] = 1/4
          this.kriteria[3].wt[2] = 4
        }
        if(val == 7) {
          this.kriteria[2].wt[3] = 1/3
          this.kriteria[3].wt[2] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text6 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[2].wt[3] = 1/2
          this.kriteria[3].wt[2] = 2
        }
        if(val == 9) {
          this.kriteria[2].wt[3] = 1
        }
        if(val == 10) {
          this.kriteria[2].wt[3] = 2
          this.kriteria[3].wt[2] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text6 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[2].wt[3] = 3
          this.kriteria[3].wt[2] = 1/3
        }
        if(val == 12) {
          this.kriteria[2].wt[3] = 4
          this.kriteria[3].wt[2] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text6 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[2].wt[3] = 5
          this.kriteria[3].wt[2] = 1/5
        }
        if(val == 14) {
          this.kriteria[2].wt[3] = 6
          this.kriteria[3].wt[2] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text6 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[2].wt[3] = 7
          this.kriteria[3].wt[2] = 1/7
        }
        if(val == 16) {
          this.kriteria[2].wt[3] = 8
          this.kriteria[3].wt[2] = 1/8
        }
      }
      if(val == 17) {
        this.text6 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[2].wt[3] = 9
          this.kriteria[3].wt[2] = 1/9
        }
      } 
    },
      test7: function(val) {
      if(val == 1) {
        this.text7 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[1].wt[4] = 1/9
        this.kriteria[4].wt[1] = 9
      }
      if(val == 3 || val == 2) {
        this.text7 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[1].wt[4] = 1/8
          this.kriteria[4].wt[1] = 8
        }
        if(val == 3) {
          this.kriteria[1].wt[4] = 1/7
          this.kriteria[4].wt[1] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text7 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[1].wt[4] = 1/6
          this.kriteria[4].wt[1] = 6
        }
        if(val == 5) {
          this.kriteria[1].wt[4] = 1/5
          this.kriteria[4].wt[1] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text7 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[1].wt[4] = 1/4
          this.kriteria[4].wt[1] = 4
        }
        if(val == 7) {
          this.kriteria[1].wt[4] = 1/3
          this.kriteria[4].wt[1] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text7 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[1].wt[4] = 1/2
          this.kriteria[4].wt[1] = 2
        }
        if(val == 9) {
          this.kriteria[1].wt[4] = 1
        }
        if(val == 10) {
          this.kriteria[1].wt[4] = 2
          this.kriteria[4].wt[1] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text7 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[1].wt[4] = 3
          this.kriteria[4].wt[1] = 1/3
        }
        if(val == 12) {
          this.kriteria[1].wt[4] = 4
          this.kriteria[4].wt[1] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text7 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[1].wt[4] = 5
          this.kriteria[4].wt[1] = 1/5
        }
        if(val == 14) {
          this.kriteria[1].wt[4] = 6
          this.kriteria[4].wt[1] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text7 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[1].wt[4] = 7
          this.kriteria[4].wt[1] = 1/7
        }
        if(val == 16) {
          this.kriteria[1].wt[4] = 8
          this.kriteria[4].wt[1] = 1/8
        }
      }
      if(val == 17) {
        this.text7 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[1].wt[4] = 9
          this.kriteria[4].wt[1] = 1/9
        }
      } 
    },
      test8: function(val) {
      if(val == 1) {
        this.text8 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[2].wt[4] = 1/9
        this.kriteria[4].wt[2] = 9
      }
      if(val == 3 || val == 2) {
        this.text8 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[2].wt[4] = 1/8
          this.kriteria[4].wt[2] = 8
        }
        if(val == 3) {
          this.kriteria[2].wt[4] = 1/7
          this.kriteria[4].wt[2] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text8 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[2].wt[4] = 1/6
          this.kriteria[4].wt[2] = 6
        }
        if(val == 5) {
          this.kriteria[2].wt[4] = 1/5
          this.kriteria[4].wt[2] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text8 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[2].wt[4] = 1/4
          this.kriteria[4].wt[2] = 4
        }
        if(val == 7) {
          this.kriteria[2].wt[4] = 1/3
          this.kriteria[4].wt[2] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text8 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[2].wt[4] = 1/2
          this.kriteria[4].wt[2] = 2
        }
        if(val == 9) {
          this.kriteria[2].wt[4] = 1
        }
        if(val == 10) {
          this.kriteria[2].wt[4] = 2
          this.kriteria[4].wt[2] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text8 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[2].wt[4] = 3
          this.kriteria[4].wt[2] = 1/3
        }
        if(val == 12) {
          this.kriteria[2].wt[4] = 4
          this.kriteria[4].wt[2] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text8 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[2].wt[4] = 5
          this.kriteria[4].wt[2] = 1/5
        }
        if(val == 14) {
          this.kriteria[2].wt[4] = 6
          this.kriteria[4].wt[2] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text8 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[2].wt[4] = 7
          this.kriteria[4].wt[2] = 1/7
        }
        if(val == 16) {
          this.kriteria[2].wt[4] = 8
          this.kriteria[4].wt[2] = 1/8
        }
      }
      if(val == 17) {
        this.text8 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[2].wt[4] = 9
          this.kriteria[4].wt[2] = 1/9
        }
      } 
    },
      test9: function(val) {
      if(val == 1) {
        this.text9 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[3].wt[4] = 1/9
        this.kriteria[4].wt[3] = 9
      }
      if(val == 3 || val == 2) {
        this.text9 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[3].wt[4] = 1/8
          this.kriteria[4].wt[3] = 8
        }
        if(val == 3) {
          this.kriteria[3].wt[4] = 1/7
          this.kriteria[4].wt[3] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text9 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[3].wt[4] = 1/6
          this.kriteria[4].wt[3] = 6
        }
        if(val == 5) {
          this.kriteria[3].wt[4] = 1/5
          this.kriteria[4].wt[3] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text9 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[3].wt[4] = 1/4
          this.kriteria[4].wt[3] = 4
        }
        if(val == 7) {
          this.kriteria[3].wt[4] = 1/3
          this.kriteria[4].wt[3] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text9 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[3].wt[4] = 1/2
          this.kriteria[4].wt[3] = 2
        }
        if(val == 9) {
          this.kriteria[3].wt[4] = 1
        }
        if(val == 10) {
          this.kriteria[3].wt[4] = 2
          this.kriteria[4].wt[3] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text9 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[3].wt[4] = 3
          this.kriteria[4].wt[3] = 1/3
        }
        if(val == 12) {
          this.kriteria[3].wt[4] = 4
          this.kriteria[4].wt[3] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text9 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[3].wt[4] = 5
          this.kriteria[4].wt[3] = 1/5
        }
        if(val == 14) {
          this.kriteria[3].wt[4] = 6
          this.kriteria[4].wt[3] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text9 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[3].wt[4] = 7
          this.kriteria[4].wt[3] = 1/7
        }
        if(val == 16) {
          this.kriteria[3].wt[4] = 8
          this.kriteria[4].wt[3] = 1/8
        }
      }
      if(val == 17) {
        this.text9 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[3].wt[4] = 9
          this.kriteria[4].wt[3] = 1/9
        }
      } 
    },
        
    },
    methods: {
        add: function() {
            let k = []
            if(this.kriteria[0].wt != []) {
                const reducer = (pr, cr) => pr + cr;
                    for(let i=0; i<this.kriteria.length; i++) {
                        k = []
                        for(let j=0; j<this.kriteria[i].wt.length; j++) {
                            let y = this.kriteria[j].wt[i]
                            k.push(y)
                        }
                        let y = k.reduce(reducer)
                        this.total.push(y)
                    }
                console.log(this.total)    
            }
        },
        comparison: function() {
            for(let x=0; x<this.kriteria.length; x++) {
                for(let y=0; y<this.kriteria[x].wt.length; y++) {
                    if(x == y) {
                        this.kriteria[x].wt[y] = 1
                    }
                }
            }

            this.kriteria[1].wt[0] = 1/this.kriteria[0].wt[1]
            this.kriteria[2].wt[0] = 1/this.kriteria[0].wt[2]
            this.kriteria[3].wt[0] = 1/this.kriteria[0].wt[3]
            this.kriteria[4].wt[0] = 1/this.kriteria[0].wt[4]

            this.kriteria[2].wt[1] = 1/this.kriteria[1].wt[2]

            this.kriteria[3].wt[1] = 1/this.kriteria[1].wt[3]
            this.kriteria[3].wt[2] = 1/this.kriteria[2].wt[3]

            this.kriteria[4].wt[1] = 1/this.kriteria[1].wt[4]
            this.kriteria[4].wt[2] = 1/this.kriteria[2].wt[4]
            this.kriteria[4].wt[3] = 1/this.kriteria[3].wt[4]
        },
        normalize: function() {
            this.add()
            this.condition = true
            const reducer = (pr, cr) => pr + cr;

            // Normalisasi dan pencarian nilai bobot
            for(let i=0; i<this.kriteria.length; i++) {
                for(let j=0; j<this.kriteria[i].wt.length; j++) {
                    let y = this.kriteria[i].wt[j]/this.total[j]
                    this.kriteria[i].nm.push(y)
                }
                this.kriteria[i].eigen = (this.kriteria[i].nm.reduce(reducer))/this.kriteria.length
            }
            
            //Meghitung Eigen Maksimum
            for(let x=0; x<this.kriteria.length;x++) {
                for(let z=0; z<this.kriteria[x].wt.length;z++) {
                    let o = this.kriteria[x].wt[z]*this.kriteria[z].eigen
                    this.kriteria[x].nEigen.push(o)
                }
                this.kriteria[x].jumlah = this.kriteria[x].nEigen.reduce(reducer)
                this.kriteria[x].lam = this.kriteria[x].jumlah/this.kriteria[x].eigen
            }


            //Normalisasi Nilai Umum pada Metode SAW
            let c1 = []
            let c2 = []
            let c3 = []
            let c4 = []
            let c5 = []
            for(let h=0; h<this.alt.length;h++) {
                this.alt[h].lm = (this.alt[h].lm>29)?0.5:this[h].lm
                this.alt[h].bi = (this.alt[h].bi<30)?0.25:0.5
                this.alt[h].kp = (this.alt[h].kp>50)?0.75:0.5
                this.alt[h].wc = (this.alt[h].wc>80)?1.0:0.75
                this.alt[h].pu = (this.alt[h].pu>50)?0.75:0.5
                
                c1.push(this.alt[h].lm)
                c2.push(this.alt[h].bi)
                c3.push(this.alt[h].kp)
                c4.push(this.alt[h].wc)
                c5.push(this.alt[h].pu)
            }

            for(let h=0; h<this.alt.length;h++) {
                this.alt[h].v = (this.alt[h].lm*this.kriteria[0].eigen) +
                            (this.alt[h].bi*this.kriteria[1].eigen) +
                            (this.alt[h].kp*this.kriteria[2].eigen) +
                            (this.alt[h].wc*this.kriteria[3].eigen) +
                            (this.alt[h].pu*this.kriteria[4].eigen)
            }
        }
    }
}
</script>

<style scoped>
    .float  {
        position:fixed;
        width:60px;
        height:60px;
        top:40px;
        right:40px;
        background-color:#0C9;
        color:#FFF;
        border-radius:50px;
        text-align:center;
        box-shadow: 2px 2px 3px #999;
    }
</style>