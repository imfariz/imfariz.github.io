<template>
    <div>
        <h1>Input Data</h1>
        <div class="input">
            <!-- <h1>Input Perbandingan</h1> -->
            <table class="table mt-5 mb-5 mx-2 table-bordered border-secondary w-45">
                <thead>
                    <tr>
                        <th>Alternatif</th>
                        <th>Perbandingan</th>
                        <th>Alternatif</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>Logika</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[0].wt[1]"></td>
                        <td>Bahasa Inggris</td>
                    </tr>
                    <tr>
                        <td>Logika</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[0].wt[2]"></td>
                        <td>Komputer</td>
                    </tr>
                    <tr>
                        <td>Logika</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[0].wt[3]"></td>
                        <td>Wawancara</td>
                    </tr>
                    <tr>
                        <td>Logika</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[0].wt[4]"></td>
                        <td>Pengetahuan Umum</td>
                    </tr>
                    <tr>
                        <td>Bahasa Inggris</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[1].wt[2]"></td>
                        <td>Komputer</td>
                    </tr>
                    <tr>
                        <td>Bahasa Inggris</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[1].wt[3]"></td>
                        <td>Wawancara</td>
                    </tr>
                    <tr>
                        <td>Bahasa Inggris</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[1].wt[4]"></td>
                        <td>Pengetahuan Umum</td>
                    </tr>
                    <tr>
                        <td>Komputer</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[2].wt[3]"></td>
                        <td>Wawancara</td>
                    </tr>
                    <tr>
                        <td>Komputer</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[2].wt[4]"></td>
                        <td>Pengetahuan Umum</td>
                    </tr>
                    <tr>
                        <td>Wawancara</td>
                        <td><input type="number" style="text-align: center" v-model="this.kriteria[3].wt[4]"></td>
                        <td>Pengetahuan Umum</td>
                    </tr>
                </tbody>
            </table>

            <!-- <h1>Data Calon Mahasiswa</h1> -->
            <table class="table table-stripped mt-5 table-bordered border-secondary w-55">
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
        </div>

         <h1 class="mt-5">Perbandingan Prioritas</h1>
            <table class="table table-stripped mt-5 mx-2 table-bordered border-secondary">
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
                    <tr>
                        <td>Total</td>
                        <td v-for="i in total" :key="i">{{ i }}</td>
                    </tr>
                </tbody>
            </table>

        <!-- <h1>Metode AHP</h1>
        <table class="table mt-5 mb-5">
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
        </table> -->

        <button class="btn btn-primary float" @click="normalize">
            N
        </button>

       
        <h1 class="mt-5">Normalisasi</h1>
        <table class="table table-stripped mt-5">
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

        <h1 class="mt-5">Nilai Bobot</h1>
        <table class="table table-stripped mt-5">
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

        <h1>Nilai Eigen Prioritas</h1>
        <table class="table table-stripped mt-5">
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
        <!-- <br><br>
        <h1>Lamda Max adalah {{ eigenMax }}</h1>
        <h1>Nilai Consistency Index adalah {{ ci }}</h1>
        <h1>Nilai Consistency Rate adalah {{ cr }}</h1>
        <h1>Bobot Prioritas {{ consistent }}</h1> -->
        
    </div>
</template>

<script>
export default {
    name: 'DataModel',
    data() {
        return {
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
            ],
            vb: []
        }
    },
    computed: {
        total: function() {
            let c = []
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
                        c.push(y)
                    }
                    
            }
                    return c
        },
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
    methods: {
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
            this.comparison()
            const reducer = (pr, cr) => pr + cr;
            
            console.log(this.kriteria[0].wt)

            // for(let x=0; x<this.kriteria.length;x++) {
            //     let i = this.kriteria[x].prioritas
            //     for(let y=0; y<this.kriteria.length;y++) {
            //         this.kriteria[y].wt.push(i/this.kriteria[y].prioritas)
            //     }
            // }

            // let wt = []
            // for(let i=0; i<this.kriteria.length; i++) {
            //     wt.push(this.kriteria[i].prioritas)
            // }
            // for(let j=0; j<this.kriteria.length; j++) {
            //     for(let k=0; k<wt.length; k++) {
            //         this.kriteria[j].wt2.push(this.kriteria[j].prioritas/wt[k])
            //     }
            //     console.log(this.kriteria[j].wt2)
            // }
            // console.log(wt)

            for(let i=0; i<this.kriteria.length; i++) {
                for(let j=0; j<this.kriteria[i].wt.length; j++) {
                    let y = this.kriteria[i].wt[j]/this.total[j]
                    this.kriteria[i].nm.push(y)
                }
                this.kriteria[i].eigen = (this.kriteria[i].nm.reduce(reducer))/this.kriteria.length
            }
            for(let x=0; x<this.kriteria.length;x++) {
                for(let z=0; z<this.kriteria[x].wt.length;z++) {
                    let o = this.kriteria[x].wt[z]*this.kriteria[z].eigen
                    this.kriteria[x].nEigen.push(o)
                }
                this.kriteria[x].jumlah = this.kriteria[x].nEigen.reduce(reducer)
                this.kriteria[x].lam = this.kriteria[x].jumlah/this.kriteria[x].eigen
            }
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
    .input {
        display: flex;
        justify-content: space-between;
    }
</style>