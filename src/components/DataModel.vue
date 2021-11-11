<template>
    <div>
        <h1>Metode AHP</h1>
        <div class="d-flex mx-4">
            <!-- <h1>Input Perbandingan</h1> -->
            <table class="table mt-5 mb-5 mx-2 table-bordered border-secondary">
                <thead>
                    <tr>
                        <th style="width:25%">Kriteria</th>
                        <th style="width:50%">Perbandingan</th>
                        <th style="width:25%">Kriteria</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Logika <br> {{ this.kriteria[0].wt[1] }}</td>
                        <td>
                            <p> {{ text }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test">
                        </td>
                        <td>Bahasa Inggris <br> {{ this.kriteria[1].wt[0] }} </td>
                    </tr>
                    <tr>
                        <td>Logika <br> {{ this.kriteria[0].wt[2] }} </td>
                        <td>
                            <p> {{ text1 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test1">
                        </td>
                        <td>Komputer <br> {{ this.kriteria[2].wt[0] }} </td>
                    </tr>
                    <tr>
                        <td>Logika <br> {{ this.kriteria[0].wt[3] }} </td>
                        <td>
                            <p> {{ text2 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test2">
                        </td>
                        <td>Wawancara <br> {{ this.kriteria[3].wt[0] }}</td>
                    </tr>
                    <tr>
                        <td>Logika <br> {{ this.kriteria[0].wt[4] }} </td>
                        <td>
                            <p> {{ text3 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test3">
                        </td>
                        <td>Pengetahuan Umum <br> {{ this.kriteria[4].wt[0] }} </td>
                    </tr>
                    <tr>
                        <td>Bahasa Inggris <br> {{ this.kriteria[1].wt[2] }} </td>
                        <td>
                            <p> {{ text4 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test4">
                        </td>
                        <td>Komputer <br> {{ this.kriteria[2].wt[1] }} </td>
                    </tr>
                    <tr>
                        <td>Bahasa Inggris <br> {{ this.kriteria[1].wt[3] }} </td>
                        <td>
                            <p> {{ text5 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test5">
                        </td>
                        <td>Wawancara <br> {{ this.kriteria[3].wt[1] }} </td>
                    </tr>
                    <tr>
                        <td>Bahasa Inggris <br> {{ this.kriteria[1].wt[4] }} </td>
                        <td>
                            <p> {{ text7 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test7">
                        </td>
                        <td>Pengetahuan Umum <br> {{ this.kriteria[4].wt[1] }} </td>
                    </tr>
                    <tr>
                        <td>Komputer <br> {{ this.kriteria[2].wt[3] }} </td>
                        <td>
                            <p> {{ text6 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test6">
                        </td>
                        <td>Wawancara <br> {{ this.kriteria[3].wt[2] }} </td>
                    </tr>
                    <tr>
                        <td>Komputer <br> {{ this.kriteria[2].wt[4] }} </td>
                        <td>
                            <p> {{ text8 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test8">
                        </td>
                        <td>Pengetahuan Umum <br> {{ this.kriteria[4].wt[2] }} </td>
                    </tr>
                    <tr>
                        <td>Wawancara <br> {{ this.kriteria[3].wt[4] }} </td>
                        <td>
                            <p> {{ text9 }}</p>
                            <input type="range" min="1" max="17" step="1" v-model="test9">
                        </td>
                        <td>Pengetahuan Umum <br> {{ this.kriteria[4].wt[3] }} </td>
                    </tr>
                </tbody>
            </table>
            <div class="align-self-center">
              <h2>(*) Menentukan Nilai Prioritas melalui Input Data dari User</h2>
              <button class="btn btn-primary mt-4 w-50" @click="normalize">Hitung</button>
            </div>
        </div>

        <!--Perhitungan SAW  -->
        <h1 class="mt-5">METODE SAW</h1>
        <section class="mx-5">
          <h1 class="mt-5 text-start">Data Calon Mahasiswa</h1>
          <table class="table table-stripped mt-5 table-bordered border-secondary">
              <thead>
                  <tr>
                      <th>Alternatif</th>
                      <th v-for="a in kriteria" :key="a">
                          {{ a.nama }}
                      </th>
                      <th v-if="condition">Vektor</th>
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
                      <td v-text="x.v" v-if="condition"></td>
                  </tr>
              </tbody>
          </table>
        </section>  

        <!-- Perhitungan AHP -->
        <div v-if="condition != false" class="mx-3">
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
            <h3 class="align-self-center ms-5 text-start">
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
            </div>
          </section>

          <section class="d-flex mx-4">
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
                          <th>Bobot</th>
                      </tr>
                  </thead>
                  <tbody>
                      <tr v-for="k in kriteria" :key="k">
                          <td v-text="k.nama"></td>
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

          <h1 class="mt-5">METODE SAW</h1>
          <section class="d-flex my-4">
            <section class="mx-5">
              <h1 class="mt-5 text-start">Data Calon Mahasiswa</h1>
              <table class="table table-stripped mt-5 table-bordered border-secondary">
                  <thead>
                      <tr>
                          <th>Alternatif</th>
                          <th v-for="a in kriteria" :key="a">
                              {{ a.nama }}
                          </th>
                      </tr>
                  </thead>
                  <tbody>
                      <tr v-for="(x, index) in c1" :key="x">
                          <td>A{{ index +1 }}</td>
                          <td>{{ c1[index] }}</td>
                          <td>{{ c2[index] }}</td>
                          <td>{{ c3[index] }}</td>
                          <td>{{ c4[index] }}</td>
                          <td>{{ c5[index] }}</td>
                      </tr>
                  </tbody>
              </table>
            </section>
            <h1 class="align-self-center ms-5 text-start">(*) Data Nilai Mahasiswa Yang Diinputkan Kemudian di Normalisasi sesuai dengan ketentuan</h1> 
          </section>

          <h1 class="mt-5 mx-5 text-start">Perhitungan SAW</h1>
          <div class="d-flex">
            <table class="table table-stripped mt-5 table-bordered border-secondary w-25 mx-5">
              <thead>
                  <tr>
                      <th>Alternatif</th>
                      <th v-if="condition">Vektor</th>
                  </tr>
              </thead>
              <tbody>
                  <tr v-for="(x, index) in alt" :key="x">
                      <td>A{{ index +1 }}</td>
                      <td v-text="x.v" v-if="condition"></td>
                  </tr>
              </tbody>
            </table>
            <h1 class="align-self-center ms-5 text-start">(*) Data yang dinormalisasi, kemudian dikalikan dengan nilai bobot sesuai dengan masing-masing kriteria</h1> 
          </div>
        </div>
        
        <!-- Floating Button -->
        <button class="btn btn-primary float" @click="show">
            S
        </button>
    </div>
</template>

<script>
export default {
    name: 'DataModel',
    data() {
        return {
            condition: false,
            test: 11,
            text: "Sedikit Lebih Penting",
            test1: 10,
            text1: "Sama Pentingnya",
            test2: 11,
            text2: "Sedikit Lebih Penting",
            test3: 11,
            text3: "Sedikit Lebih Penting",
            test4: 11,
            text4: "Sedikit Lebih Penting",
            test5: 10,
            text5: "Sama Pentingnya",
            test6: 10,
            text6: "Sama Pentingnya",
            test7: 11,
            text7: "Sedikit Lebih Penting",
            test8: 11,
            text8: "Sedikit Lebih Penting",
            test9: 10,
            text9: "Sama Pentingnya",
            total: [1,1,1,1,1],
            c1: [1,1,1,1],
            c2: [1,1,1,1],
            c3: [1,1,1,1],
            c4: [1,1,1,1],
            c5: [1,1,1,1],
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
                    wt: [1, 3, 2, 3, 3],
                    nm: [1, 1, 1, 1, 1],
                    eigen: 0,
                    nEigen: [],
                    jumlah: 0,
                    lam: 0
                },
                {
                    nama: 'Bahasa Inggris',
                    wt: [0.333, 1, 3, 2, 3],
                    nm: [1, 1, 1, 1, 1],
                    eigen: 0,
                    nEigen: [],
                    jumlah: 0,
                    lam: 0
                },
                {
                    nama: 'Komputer',
                    wt: [0.5, 0.333, 1, 2, 3],
                    nm: [1, 1, 1, 1, 1],
                    eigen: 0,
                    nEigen: [],
                    jumlah: 0,
                    lam: 0
                },
                {
                    nama: 'Wawancara',
                    wt: [0.333, 0.5, 0.5, 1, 2],
                    nm: [1, 1, 1, 1, 1],
                    eigen: 0,
                    nEigen: [],
                    jumlah: 0,
                    lam: 0
                },
                {
                    nama: 'Pengetahuan Umum',
                    wt: [0.333, 0.333, 0.333, 0.5, 1],
                    nm: [1, 1, 1, 1, 1],
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
                        this.total[i] = y
                    }  
            }
        },
        show: function() {
            if(!this.condition) {
              this.condition = true
            } else {
              this.condition = false
            }          
        },
        ahp: function() {
            this.add()
            // this.show()
            const reducer = (pr, cr) => pr + cr;

            // Normalisasi dan pencarian nilai bobot
            for(let i=0; i<this.kriteria.length; i++) {
                for(let j=0; j<this.kriteria[i].wt.length; j++) {
                    let y = this.kriteria[i].wt[j]/this.total[j]
                    this.kriteria[i].nm[j] = y
                }
                this.kriteria[i].eigen = (this.kriteria[i].nm.reduce(reducer))/this.kriteria.length
            }
            
            //Meghitung Eigen Maksimum
            for(let x=0; x<this.kriteria.length;x++) {
                for(let z=0; z<this.kriteria[x].wt.length;z++) {
                    let o = this.kriteria[x].wt[z]*this.kriteria[z].eigen
                    this.kriteria[x].nEigen[z] = o
                }
                this.kriteria[x].jumlah = this.kriteria[x].nEigen.reduce(reducer)
                this.kriteria[x].lam = this.kriteria[x].jumlah/this.kriteria[x].eigen
            }
        },
        saw: function() {
            //Normalisasi Nilai Umum pada Metode SAW
            for(let h=0; h<this.alt.length;h++) {
                this.c1[h] = (this.alt[h].lm>29)?0.5:this.alt[h].lm
                this.c2[h] = (this.alt[h].bi<30)?0.25:0.5
                this.c3[h] = (this.alt[h].kp>50)?0.75:0.5
                this.c4[h] = (this.alt[h].wc>80)?1.0:0.75
                this.c5[h] = (this.alt[h].pu>50)?0.75:0.5
            }

            console.log(this.c1)

            for(let h=0; h<this.alt.length;h++) {
                this.alt[h].v = (this.c1[h]*this.kriteria[0].eigen) +
                            (this.c2[h]*this.kriteria[1].eigen) +
                            (this.c3[h]*this.kriteria[2].eigen) +
                            (this.c4[h]*this.kriteria[3].eigen) +
                            (this.c5[h]*this.kriteria[4].eigen)
            }

        },
        normalize: function() {
          this.ahp()
          this.saw()
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