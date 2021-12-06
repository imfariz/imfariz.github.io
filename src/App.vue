<template>
    <div>
        <div class="d-flex content">
            <div class="p-4 alternative d-flex flex-column justify-content-center">
            <div class="title ms-2">
                <div class="top d-flex justify-content-between w-100 align-items-center">
                    <h1>Top Candidates</h1>
                    <div class="icon">
                        <button class="cta cta-secondary me-4" @click="showingCdt">
                            CANDIDATES
                        </button>
                        <button class="cta cta-secondary" @click="showingCr">
                            CRITERIAS
                        </button>
                    </div>
                </div>
                <h2>Candidates has been ranked by their subject score. <br>The scores that accumulated with AHP method then being ranked with SAW method. </h2>
            </div>
            <div class="lists d-flex flex-column justify-content-around mt-4">
                <div class="list d-flex align-items-end" v-for="(alt,index) in result.alt" :key="alt">
                    <p class="rank ms-2" v-text="index +1"></p>
                    <p class="name ms-2" v-text="alt.nama"></p>
                    <p class="score me-2" v-text="Number((alt.value).toFixed(3))"></p>
                </div>
            </div>
            </div>
            <div class="p-4 criteria d-flex flex-column justify-content-center">
            <div class="title ms-2">
                <div class="top d-flex justify-content-between w-100 align-items-center">
                    <h1>Top Criteria</h1>
                    <Icon icon="ph:gear-light" class="crt" @click="showingCrt" />    
                </div>
                <h2>Criteria that given by user will be accumulating with <br> AHP method to find the most potential criteria </h2>
            </div>
            <div class="lists d-flex flex-column justify-content-around mt-4">
                <div class="list d-flex align-items-end" v-for="(crt, index) in result.crt" :key="crt">
                    <p class="rank ms-2" v-text="index+1"></p>
                    <p class="name ms-2" v-text="crt.nama"></p>
                    <p class="score me-2" v-text="Number((crt.bobotPrioritas).toFixed(3))"></p>
                </div>
            </div>
            </div>
        </div>

        <!-- Modal -->
        <modal-candidate @switch="fillCriteria($event)" @checked="showingCrt" :crt="kriteria" v-if="closed==true" :prioValue="priorityValue" />

        <transition name="MC">
            <modal-criteria name="fade" @checked="showingCr" :bobot="kriteria" v-if="closeCrt==true" />
        </transition>

        <transition name="MA">
            <modal-alternative @switch="fillAlternative($event)" @checked="showingCdt" :alt="alternative" v-if="closeCdt==true" />
        </transition>
    </div>
</template>

<script>

import { Icon } from '@iconify/vue';
import ModalCandidate from './components/ModalCandidate';
import ModalCriteria from './components/ModalCriteria.vue';
import ModalAlternative from './components/ModalAlternative.vue'

export default {
  name: 'App',
  components: {
    Icon,
    ModalCandidate,
    ModalCriteria,
    ModalAlternative
  },
  mounted() {
    this.finishing()
  },
  data() {
      return {
        //Watch Properties
        priorityValue: [11,10,11,11,11,10,11,10,11,10],

        //   Modal Variables
        closed: false,
        closeCdt: false,
        closeCrt: false,

        // Data Variables
        alternative: [
            {
                nama: "Fariz Ramadhan",
                logma: 32.5,
                english: 35,
                computer: 50,
                interview: 75,
                general: 35,
                value: 1
            },
            {
                nama: "Nabila Fitriana",
                logma: 42.5,
                english: 30,
                computer: 55,
                interview: 72.9,
                general: 60,
                value: 1
            },
            {
                nama: "Yessica Tamara",
                logma: 42.5,
                english: 35,
                computer: 60,
                interview: 83.6,
                general: 40,
                value: 1
            },
            {
                nama: "Azizi Shafa Asadel",
                logma: 30,
                english: 15,
                computer: 50,
                interview: 81.4,
                general: 45,
                value: 1
            },
        ],
        kriteria: [
            {
                nama: "Logika Matematika",
                bobot: [1, 3, 2, 3, 3],
                normal: [1,1,1,1,1],
                bobotPrioritas: 0,
                normalEigen: [],
                jumlah: 0,
                eigen: 0
            },
            {
                nama: "Bahasa Inggris",
                bobot: [0.333, 1, 3, 2, 3],
                normal: [1,1,1,1,1],
                bobotPrioritas: 0,
                normalEigen: [],
                jumlah: 0,
                eigen: 0
            },
            {
                nama: "Komputer",
                bobot: [0.5, 0.333, 1, 2, 3],
                normal: [1,1,1,1,1],
                bobotPrioritas: 0,
                normalEigen: [],
                jumlah: 0,
                eigen: 0
            },
            {
                nama: "Wawancara",
                bobot: [0.333, 0.5, 0.5, 1, 2],
                normal: [1,1,1,1,1],
                bobotPrioritas: 0,
                normalEigen: [],
                jumlah: 0,
                eigen: 0
            },
            {
                nama: "Pengetahuan Umum",
                bobot: [0.333, 0.333, 0.333, 0.5, 1],
                normal: [1,1,1,1,1],
                bobotPrioritas: 0,
                normalEigen: [],
                jumlah: 0,
                eigen: 0
            }
        ],

        // Utility
        totalKriteria: [1,1,1,1,1],
        criteria1: [1,1,1,1],
        criteria2: [1,1,1,1],
        criteria3: [1,1,1,1],
        criteria4: [1,1,1,1],
        criteria5: [1,1,1,1],

        //Ranked
        result: {
            alt: [],
            crt: []
        }
    }
},
watch: {
    closed: function(val) {
        if(val == false) {
            this.finishing()
        }
    },
    closeCdt: function(val) {
        if(val == false) {
            this.finishing()
        }
    }
},
methods: {
    showingCrt : function() {
        if(this.closed == true){
            this.closed = false
        } else {
            this.closed = true
        }
    },
    showingCdt: function() {
    if(this.closeCdt == true){
            this.closeCdt = false
        } else {
            this.closeCdt = true
        }
    },
    showingCr: function() {
    if(this.closeCrt == true){
            this.closeCrt = false
        } else {
            this.closeCrt = true
        }
    },
    fillCriteria: function(value) {
        this.kriteria = value.kriteria
        this.priorityValue = value.priority
    },
    fillAlternative: function(value) {
        this.alternative = value
    },

    //  Algoritma
    totalizing: function() {
        let k = []
            if(this.kriteria[0].bobot != []) {
                const reducer = (pr, cr) => pr + cr;
                    for(let i=0; i<this.kriteria.length; i++) {
                        k = []
                        for(let j=0; j<this.kriteria[i].bobot.length; j++) {
                            let y = this.kriteria[j].bobot[i]
                            k.push(y)
                        }
                        let y = k.reduce(reducer)
                        this.totalKriteria[i] = y
                    }  
            }
    },
    ahp: function() {
    this.totalizing()
    const reducer = (previous, current) => previous + current;

    // Normalisasi dan pencarian nilai bobot
    for(let i=0; i<this.kriteria.length; i++) {
        for(let j=0; j<this.kriteria[i].bobot.length; j++) {
            let y = this.kriteria[i].bobot[j]/this.totalKriteria[j]
            this.kriteria[i].normal[j] = y
        }
        this.kriteria[i].bobotPrioritas = (this.kriteria[i].normal.reduce(reducer))/this.kriteria.length
    }

    //Meghitung Eigen Maksimum
    for(let x=0; x<this.kriteria.length;x++) {
        for(let z=0; z<this.kriteria[x].bobot.length;z++) {
            let o = this.kriteria[x].bobot[z]*this.kriteria[z].bobotPrioritas
            this.kriteria[x].normalEigen[z] = o
        }
        this.kriteria[x].jumlah = this.kriteria[x].normalEigen.reduce(reducer)
        this.kriteria[x].eigen = this.kriteria[x].jumlah/this.kriteria[x].bobotPrioritas
    }

    // Ranking
    // this.kriteria.sort((a,b) => parseFloat(b.eigen) - parseFloat(a.eigen))
    },
    saw: function() {
        //Normalisasi Nilai Umum pada Metode SAW
        for(let h=0; h<this.alternative.length;h++) {
            this.criteria1[h] = (this.alternative[h].logma>29)?0.5:this.alternative[h].logma
            this.criteria2[h] = (this.alternative[h].english<30)?0.25:0.5
            this.criteria3[h] = (this.alternative[h].computer>50)?0.75:0.5
            this.criteria4[h] = (this.alternative[h].interview>80)?1.0:0.75
            this.criteria5[h] = (this.alternative[h].general>50)?0.75:0.5
        }

        for(let h=0; h<this.alternative.length;h++) {
            this.alternative[h].value = (this.criteria1[h]*this.kriteria[0].bobotPrioritas) +
                (this.criteria2[h]*this.kriteria[1].bobotPrioritas) +
                (this.criteria3[h]*this.kriteria[2].bobotPrioritas) +
                (this.criteria4[h]*this.kriteria[3].bobotPrioritas) +
                (this.criteria5[h]*this.kriteria[4].bobotPrioritas)
        }

        //Ranking
        // this.alternative.sort((a,b) => parseFloat(b.value) - parseFloat(a.value))
    },
    finishing: function() {
        this.ahp()
        this.saw()

        //Ranking
        this.result.crt = this.kriteria.sort((a,b) => parseFloat(b.bobotPrioritas) - parseFloat(a.bobotPrioritas))
        this.result.alt = this.alternative.sort((a,b) => parseFloat(b.value) - parseFloat(a.value))
    }
}
}
</script>

<style>
#app {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  height: 100vh;
}

h1, h2, h3, h4, h5 {
    font-family: 'Poppins', sans-serif;
}
p {
    font-family: 'Lato', sans-serif;
}
.content {
  height: 100vh;
}

.score {
    margin-left: auto;
}

.lists {
    width: 100%;
    height: 345px;
    height: max-content;
}

button.cta-secondary {
    background-color: transparent;
    color: #070707;
    border: solid 2px #070707;
}

button.cta-secondary:hover {
    color: #FCFCFC;
    background-color: #070707;
    border: none;
}

/* Model Cdt */
.model-cdt {
    position: absolute; 
    z-index: 2;
    left: 0;
    top: 0;
    width: 100%; 
    height: 100%;
    overflow: hidden;
    background-color: rgba(0,0,0,0.7); 
}

.model-crt {
    position: absolute; 
    z-index: 4;
    left: 0;
    top: 0;
    width: 100%; 
    height: 100%;
    overflow: hidden;
    background-color: rgba(255, 255, 255, 0.7); 
}

.model-cdt button.close{
    position: absolute;
    z-index: 4;
    background-color: #FCFCFC;
    border-radius: 50%;
    top: 50%;
    right: 8%;
    width: 70px;
    height: 70px;
    border: solid 2px #070707;
    transform: rotate(180deg);
    animation-name: rotate;
    animation-duration: 250ms;
}

.model-crt button.close{
    position: absolute;
    z-index: 4;
    background-color: #FCFCFC;
    border-radius: 50%;
    top: 50%;
    left: 8%;
    width: 70px;
    height: 70px;
    border: solid 2px #070707;
    transform: rotate(0deg);
    animation-name: rotateRev;
    animation-duration: 250ms;
}

.model-cdt button.close:hover{
    animation-name: rotateRev;
    animation-duration: 250ms;
    transform: rotate(0deg);
}

.model-crt button.close:hover{
    animation-name: rotate;
    animation-duration: 250ms;
    transform: rotate(180deg);
}

.model-cdt-content {
    width: 90%;
    height: 100%;
    background-color: #FCFCFC;
}

.model-crt-content {
    width: 90%;
    height: 100%;
    padding: 40px;
    padding-left: 7%;
    background-color: #070707;
    color: #FCFCFC;
}

.model-cdt-table {
    font-family: 'Poppins', sans-serif;
    font-weight: bold;
}

.model-crt-table {
    font-family: 'Poppins', sans-serif;
    font-weight: bold;
}

.model-cdt-table tbody::before {
    content: '';
    display: table-row;
    height: 20px;
    border-bottom: solid 4px #070707;
}

.model-crt-table tbody::before {
    content: '';
    display: table-row;
    height: 20px;
    border-bottom: solid 4px #FCFCFC;
}

.model-cdt-table tbody {
    border-bottom: solid 4px #070707;
}

.model-cdt-table tbody td {
    padding: 20px 0;
}


.model-cdt-table tbody input {
    border: none;
}

.model-cdt-table tbody input:hover {
    border-bottom: 2px solid #070707;
}

.model-crt-table tbody {
    border-bottom: solid 4px #FCFCFC;
}

.model-crt-table tbody td {
    padding: 20px 0;
}


.model-crt-table tbody input {
    border: none;
    background-color: transparent;
    color: #FCFCFC;
}

.model-crt-table tbody input:hover {
    border-bottom: 2px solid #FCFCFC;
}

.model-crt-cta button.cta-primary {
    color: #070707;
    background-color: #FCFCFC;
}

/* Alternatives */
.title h1 {
    font-weight: bold;
}
.alternative h2 {
    font-size: 12px;
    color: #9f9f9f;
}
.alternative p {
    font-size: 24px;
    color: #FCFCFC;
    font-weight: bold;
}
.alternative .rank {
    width: 38px;
    height: 38px;
    text-align: center;
    border-radius: 50%;
    border: solid 2px #fcfcfc
}
.alternative .list {
    background-color: #070707;
    height: 65px;
    margin-bottom: 15px;
    box-shadow: 0 4px 4px #070707 ;
}
.alternative {
    background-color: #FCFCFC;
    width: 60%;
    height: 100%;
}

.top .alt {
    color: #070707;
    font-size: 40px;
}

.top .alt:hover {
    font-size: 50px;
}

/* Criteria */
.criteria .title h1 {
    color: #FCFCFC;
    font-weight: bold;
}
.criteria h2 {
    font-size: 12px;
    color: #9f9f9f;
}
.criteria p {
    font-size: 24px;
    color: #070707;
    font-weight: bold;
}
.criteria {
    background-color: #070707;
    width: 60%;
    height: 100%;
}
.criteria .rank {
    width: 38px;
    height: 38px;
    text-align: center;
    border-radius: 50%;
    border: solid 2px #070707
}
.criteria .list {
    background-color: #FCFCFC;
    height: 65px;
    margin-bottom: 15px;
    box-shadow: 0 4px 4px #FCFCFC ;
}
.criteria .top .crt {
    color: #FCFCFC;
    font-size: 40px;
}
.criteria .top .crt:hover {
    animation-name: spin;
    animation-duration: 4000ms;
    animation-iteration-count: infinite;
    animation-timing-function: linear;
}

/* Modal */
.model button.close {
    position: absolute;
    top: 0;
    margin-top: 15px;
    margin-left: 670px;
    font-size: 40px;
    border: none;
    background-color: transparent;
}

.model button.close:hover {
    font-size: 50px;
}

.model-content {
    margin: auto;
    width: 50%;
    height: 90%;
    background-color: #FCFCFC;
}

.model-content-title h5 {
    font-size: 24px;
    font-weight: bold;
}

.model-content-title p {
    font-family: 'Poppins', sans-serif;
    font-size: 12px;
    color: #9f9f9f;
}

.model-content-input {
    overflow: scroll;
    margin-bottom: 20px;
}

.input-list {
    height: 60px;
}

.input-list .input-slide {
    font-size: 12px;
    color: #9f9f9f;
    width: 30%;
}

.nput-list .input-slide input {
    background-color: #070707;
}

.input-list .input-slide p {
    margin-bottom: 3px;
}

.model-content-input .subject {
    font-family: 'Poppins', sans-serif;
    text-transform: uppercase;
    font-size: 16px;
    font-weight: bold;
    width: 25%;
}

.cta {
    height: 48px;
    width: 120px;
    border: none;
}

.cta-primary {
    color: #FCFCFC;
    background-color: #070707;
}

/* Animation */

/* Entering Page */
.MC-enter-active {
    animation: fadedMC 500ms ease;
}

.MA-enter-active {
    animation: fadedMA 500ms ease;
}

/* Leaving Page */
.MC-leave-active {
    animation: fadedMC 500ms ease reverse;
}

.MA-leave-active {
    animation: fadedMA 500ms ease reverse;
}

@keyframes fadedMC {
    from {transform: translateX(100%);}
    to {transform: translateX(0);}
}

@keyframes fadedMA {
    from {transform: translateX(-100%);}
    to {transform: translateX(0);}
}

@keyframes spin {
    from {
        transform: rotate(0deg);
    } to {
        transform: rotate(360deg)
    }
}

@keyframes rotate {
    from {
        transform: rotate(0deg);
    } to {
        transform: rotate(180deg);
    }
}

@keyframes rotateRev {
    from {
        transform: rotate(180deg);
    } to {
        transform: rotate(0deg);
    }
}
</style>
