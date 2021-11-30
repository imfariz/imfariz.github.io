<template>
    <div class="model">
        <div class="model-content mt-4 d-flex flex-column align-items-center">
            <div class="model-content-title text-center mt-4">
                <h5>CRITERIA</h5>
                <p>Slide the circle to give criteria’s value priority.</p>
            </div>
            <div class="model-content-input w-100 mt-4">
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Logika Matematika <br> {{ this.kriteria[0].bobot[1] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text0 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test0">
                    </div>
                    <div class="subject">
                        <p>Bahasa Inggris <br> {{ this.kriteria[1].bobot[0] }}</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Logika Matematika <br> {{ this.kriteria[0].bobot[2] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text1 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test1">
                    </div>
                    <div class="subject">
                        <p>Komputer <br> {{ this.kriteria[2].bobot[0] }}</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Logika Matematika <br> {{ this.kriteria[0].bobot[3] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text2 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test2">
                    </div>
                    <div class="subject">
                        <p>Wawancara <br> {{ this.kriteria[3].bobot[0] }}</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Logika Matematika <br> {{ this.kriteria[0].bobot[4] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text3 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test3">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum <br> {{ this.kriteria[4].bobot[0] }}</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Bahasa Inggris <br> {{ this.kriteria[1].bobot[2] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text4 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test4">
                    </div>
                    <div class="subject">
                        <p>Komputer <br> {{ this.kriteria[2].bobot[1] }}</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Bahasa Inggris <br> {{ this.kriteria[1].bobot[3] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text5 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test5">
                    </div>
                    <div class="subject">
                        <p>Wawancara <br> {{ this.kriteria[3].bobot[1] }}</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Bahasa Inggris <br> {{ this.kriteria[1].bobot[4] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text6 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test6">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum <br> {{ this.kriteria[4].bobot[1] }}</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Komputer <br> {{ this.kriteria[2].bobot[3] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text7 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test7">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum <br> {{ this.kriteria[3].bobot[2] }}</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Komputer <br> {{ this.kriteria[2].bobot[4] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text8 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test8">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum <br> {{ this.kriteria[4].bobot[2] }}</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Wawancara <br> {{ this.kriteria[3].bobot[4] }}</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>{{ text9 }}</p>
                        <input type="range" min="1" max="17" step="1" v-model="test9">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum <br> {{ this.kriteria[4].bobot[3] }}</p>
                    </div>
                </div>
            </div>
            <div class="model-cta mt-auto mb-5 align-self-end me-5">
                <button class="cta cta-primary" @click="test">SAVE</button>
            </div>
            <button class="close" @click="$emit('checked')">
                <Icon icon="radix-icons:cross-2" />
            </button>
        </div>        
    </div>
</template>

<script>

import {Icon} from '@iconify/vue'

export default {
    name: 'ModalCandidate',
    components: {
        Icon
    },
    props: {
      crt: Array
    },
    created() {
      this.kriteria = this.crt
    },
    data() {
        return {
            // Priority
            test0: 10,
            test1: 10,
            test2: 10,
            test3: 10,
            test4: 10,
            test5: 10,
            test6: 10,
            test7: 10,
            test8: 10,
            test9: 10,

            // Priority Text
            text0: "Sama Pentingnya",
            text1: "Sama Pentingnya",
            text2: "Sama Pentingnya",
            text3: "Sama Pentingnya",
            text4: "Sama Pentingnya",
            text5: "Sama Pentingnya",
            text6: "Sama Pentingnya",
            text7: "Sama Pentingnya",
            text8: "Sama Pentingnya",
            text9: "Sama Pentingnya",

            // Data Priority
            kriteria: [],
        }
    },
    watch: {
        test0: function(val) {
        if(val == 1) {
            this.text0 = "Mutlak Tidak Lebih Penting dari"
            this.kriteria[0].bobot[1] = 1/9
            this.kriteria[1].bobot[0] = 9
        }
        if(val == 3 || val == 2) {
            this.text0 = "Sangat Tidak Lebih Penting dari"
            if(val == 2) {
            this.kriteria[0].bobot[1] = 1/8
            this.kriteria[1].bobot[0] = 8
            }
            if(val == 3) {
            this.kriteria[0].bobot[1] = 1/7
            this.kriteria[1].bobot[0] = 7
            }
        }
        if(val == 5 || val == 4) {
            this.text0 = "Tidak Lebih Penting dari"
            if(val == 4) {
            this.kriteria[0].bobot[1] = 1/6
            this.kriteria[1].bobot[0] = 6
            }
            if(val == 5) {
            this.kriteria[0].bobot[1] = 1/5
            this.kriteria[1].bobot[0] = 5
            }
        }
        if(val == 7 || val == 6) {
            this.text0 = "Sedikit Tidak Lebih Penting dari"
            if(val == 6) {
            this.kriteria[0].bobot[1] = 1/4
            this.kriteria[1].bobot[0] = 4
            }
            if(val == 7) {
            this.kriteria[0].bobot[1] = 1/3
            this.kriteria[1].bobot[0] = 3
            }
        }
        if(val == 9 || val == 8 || val == 10) {
            this.text0 = "Sama Pentingnya"
            if(val == 8) {
            this.kriteria[0].bobot[1] = 1/2
            this.kriteria[1].bobot[0] = 2
            }
            if(val == 9) {
            this.kriteria[0].bobot[1] = 1
            }
            if(val == 10) {
            this.kriteria[0].bobot[1] = 2
            this.kriteria[1].bobot[0] = 1/2
            }
        }
        if(val == 11 || val == 12) {
            this.text0 = "Sedikit Lebih Penting dari"
            if(val == 11) {
            this.kriteria[0].bobot[1] = 3
            this.kriteria[1].bobot[0] = 1/3
            }
            if(val == 12) {
            this.kriteria[0].bobot[1] = 4
            this.kriteria[1].bobot[0] = 1/4
            }
        }
        if(val == 13 || val == 14) {
            this.text0 = "Lebih Penting dari"
            if(val == 13) {
            this.kriteria[0].bobot[1] = 5
            this.kriteria[1].bobot[0] = 1/5
            }
            if(val == 14) {
            this.kriteria[0].bobot[1] = 6
            this.kriteria[1].bobot[0] = 1/6
            }
        }
        if(val == 15 || val == 16) {
            this.text0 = "Sangat Lebih Penting dari"
            if(val == 15) {
            this.kriteria[0].bobot[1] = 7
            this.kriteria[1].bobot[0] = 1/7
            }
            if(val == 16) {
            this.kriteria[0].bobot[1] = 8
            this.kriteria[1].bobot[0] = 1/8
            }
        }
        if(val == 17) {
            this.text0 = "Mutlak Lebih Penting dari"
            if(val == 17) {
            this.kriteria[0].bobot[1] = 9
            this.kriteria[1].bobot[0] = 1/9
            }
        } 
    },
        test1: function(val) {
        if(val == 1) {
            this.text1 = "Mutlak Tidak Lebih Penting dari"
            this.kriteria[0].bobot[2] = 1/9
            this.kriteria[2].bobot[0] = 9
        }
        if(val == 3 || val == 2) {
            this.text1 = "Sangat Tidak Lebih Penting dari"
            if(val == 2) {
            this.kriteria[0].bobot[2] = 1/8
            this.kriteria[2].bobot[0] = 8
            }
            if(val == 3) {
            this.kriteria[0].bobot[2] = 1/7
            this.kriteria[2].bobot[0] = 7
            }
        }
        if(val == 5 || val == 4) {
            this.text1 = "Tidak Lebih Penting dari"
            if(val == 4) {
            this.kriteria[0].bobot[2] = 1/6
            this.kriteria[2].bobot[0] = 6
            }
            if(val == 5) {
            this.kriteria[0].bobot[2] = 1/5
            this.kriteria[2].bobot[0] = 5
            }
        }
        if(val == 7 || val == 6) {
            this.text1 = "Sedikit Tidak Lebih Penting dari"
            if(val == 6) {
            this.kriteria[0].bobot[2] = 1/4
            this.kriteria[2].bobot[0] = 4
            }
            if(val == 7) {
            this.kriteria[0].bobot[2] = 1/3
            this.kriteria[2].bobot[0] = 3
            }
        }
        if(val == 9 || val == 8 || val == 10) {
            this.text1 = "Sama Pentingnya"
            if(val == 8) {
            this.kriteria[0].bobot[2] = 1/2
            this.kriteria[2].bobot[0] = 2
            }
            if(val == 9) {
            this.kriteria[0].bobot[2] = 1
            }
            if(val == 10) {
            this.kriteria[0].bobot[2] = 2
            this.kriteria[2].bobot[0] = 1/2
            }
        }
        if(val == 11 || val == 12) {
            this.text1 = "Sedikit Lebih Penting dari"
            if(val == 11) {
            this.kriteria[0].bobot[2] = 3
            this.kriteria[2].bobot[0] = 1/3
            }
            if(val == 12) {
            this.kriteria[0].bobot[2] = 4
            this.kriteria[2].bobot[0] = 1/4
            }
        }
        if(val == 13 || val == 14) {
            this.text1 = "Lebih Penting dari"
            if(val == 13) {
            this.kriteria[0].bobot[2] = 5
            this.kriteria[2].bobot[0] = 1/5
            }
            if(val == 14) {
            this.kriteria[0].bobot[2] = 6
            this.kriteria[2].bobot[0] = 1/6
            }
        }
        if(val == 15 || val == 16) {
            this.text1 = "Sangat Lebih Penting dari"
            if(val == 15) {
            this.kriteria[0].bobot[2] = 7
            this.kriteria[2].bobot[0] = 1/7
            }
            if(val == 16) {
            this.kriteria[0].bobot[2] = 8
            this.kriteria[2].bobot[0] = 1/8
            }
        }
        if(val == 17) {
            this.text1 = "Mutlak Lebih Penting dari"
            if(val == 17) {
            this.kriteria[0].bobot[2] = 9
            this.kriteria[2].bobot[0] = 1/9
            }
        } 
    },
        test2: function(val) {
      if(val == 1) {
        this.text2 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[0].bobot[3] = 1/9
        this.kriteria[3].bobot[0] = 9
      }
      if(val == 3 || val == 2) {
        this.text2 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[0].bobot[3] = 1/8
          this.kriteria[3].bobot[0] = 8
        }
        if(val == 3) {
          this.kriteria[0].bobot[3] = 1/7
          this.kriteria[3].bobot[0] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text2 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[0].bobot[3] = 1/6
          this.kriteria[3].bobot[0] = 6
        }
        if(val == 5) {
          this.kriteria[0].bobot[3] = 1/5
          this.kriteria[3].bobot[0] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text2 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[0].bobot[3] = 1/4
          this.kriteria[3].bobot[0] = 4
        }
        if(val == 7) {
          this.kriteria[0].bobot[3] = 1/3
          this.kriteria[3].bobot[0] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text2 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[0].bobot[3] = 1/2
          this.kriteria[3].bobot[0] = 2
        }
        if(val == 9) {
          this.kriteria[0].bobot[3] = 1
        }
        if(val == 10) {
          this.kriteria[0].bobot[3] = 2
          this.kriteria[3].bobot[0] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text2 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[0].bobot[3] = 3
          this.kriteria[3].bobot[0] = 1/3
        }
        if(val == 12) {
          this.kriteria[0].bobot[3] = 4
          this.kriteria[3].bobot[0] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text2 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[0].bobot[3] = 5
          this.kriteria[3].bobot[0] = 1/5
        }
        if(val == 14) {
          this.kriteria[0].bobot[3] = 6
          this.kriteria[3].bobot[0] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text2 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[0].bobot[3] = 7
          this.kriteria[3].bobot[0] = 1/7
        }
        if(val == 16) {
          this.kriteria[0].bobot[3] = 8
          this.kriteria[3].bobot[0] = 1/8
        }
      }
      if(val == 17) {
        this.text2 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[0].bobot[3] = 9
          this.kriteria[3].bobot[0] = 1/9
        }
      } 
    },
      test3: function(val) {
      if(val == 1) {
        this.text3 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[0].bobot[4] = 1/9
        this.kriteria[4].bobot[0] = 9
      }
      if(val == 3 || val == 2) {
        this.text3 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[0].bobot[4] = 1/8
          this.kriteria[4].bobot[0] = 8
        }
        if(val == 3) {
          this.kriteria[0].bobot[4] = 1/7
          this.kriteria[4].bobot[0] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text3 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[0].bobot[4] = 1/6
          this.kriteria[4].bobot[0] = 6
        }
        if(val == 5) {
          this.kriteria[0].bobot[4] = 1/5
          this.kriteria[4].bobot[0] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text3 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[0].bobot[4] = 1/4
          this.kriteria[4].bobot[0] = 4
        }
        if(val == 7) {
          this.kriteria[0].bobot[4] = 1/3
          this.kriteria[4].bobot[0] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text3 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[0].bobot[4] = 1/2
          this.kriteria[4].bobot[0] = 2
        }
        if(val == 9) {
          this.kriteria[0].bobot[4] = 1
        }
        if(val == 10) {
          this.kriteria[0].bobot[4] = 2
          this.kriteria[4].bobot[0] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text3 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[0].bobot[4] = 3
          this.kriteria[4].bobot[0] = 1/3
        }
        if(val == 12) {
          this.kriteria[0].bobot[4] = 4
          this.kriteria[4].bobot[0] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text3 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[0].bobot[4] = 5
          this.kriteria[4].bobot[0] = 1/5
        }
        if(val == 14) {
          this.kriteria[0].bobot[4] = 6
          this.kriteria[4].bobot[0] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text3 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[0].bobot[4] = 7
          this.kriteria[4].bobot[0] = 1/7
        }
        if(val == 16) {
          this.kriteria[0].bobot[4] = 8
          this.kriteria[4].bobot[0] = 1/8
        }
      }
      if(val == 17) {
        this.text3 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[0].bobot[4] = 9
          this.kriteria[4].bobot[0] = 1/9
        }
      } 
    },
      test4: function(val) {
      if(val == 1) {
        this.text4 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[1].bobot[2] = 1/9
        this.kriteria[2].bobot[1] = 9
      }
      if(val == 3 || val == 2) {
        this.text4 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[1].bobot[2] = 1/8
          this.kriteria[2].bobot[1] = 8
        }
        if(val == 3) {
          this.kriteria[1].bobot[2] = 1/7
          this.kriteria[2].bobot[1] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text4 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[1].bobot[2] = 1/6
          this.kriteria[2].bobot[1] = 6
        }
        if(val == 5) {
          this.kriteria[1].bobot[2] = 1/5
          this.kriteria[2].bobot[1] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text4 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[1].bobot[2] = 1/4
          this.kriteria[2].bobot[1] = 4
        }
        if(val == 7) {
          this.kriteria[1].bobot[2] = 1/3
          this.kriteria[2].bobot[1] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text4 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[1].bobot[2] = 1/2
          this.kriteria[2].bobot[1] = 2
        }
        if(val == 9) {
          this.kriteria[1].bobot[2] = 1
        }
        if(val == 10) {
          this.kriteria[1].bobot[2] = 2
          this.kriteria[2].bobot[1] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text4 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[1].bobot[2] = 3
          this.kriteria[2].bobot[1] = 1/3
        }
        if(val == 12) {
          this.kriteria[1].bobot[2] = 4
          this.kriteria[2].bobot[1] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text4 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[1].bobot[2] = 5
          this.kriteria[2].bobot[1] = 1/5
        }
        if(val == 14) {
          this.kriteria[1].bobot[2] = 6
          this.kriteria[2].bobot[1] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text4 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[1].bobot[2] = 7
          this.kriteria[2].bobot[1] = 1/7
        }
        if(val == 16) {
          this.kriteria[1].bobot[2] = 8
          this.kriteria[2].bobot[1] = 1/8
        }
      }
      if(val == 17) {
        this.text4 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[1].bobot[2] = 9
          this.kriteria[2].bobot[1] = 1/9
        }
      } 
    },
      test5: function(val) {
      if(val == 1) {
        this.text5 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[1].bobot[3] = 1/9
        this.kriteria[3].bobot[1] = 9
      }
      if(val == 3 || val == 2) {
        this.text5 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[1].bobot[3] = 1/8
          this.kriteria[3].bobot[1] = 8
        }
        if(val == 3) {
          this.kriteria[1].bobot[3] = 1/7
          this.kriteria[3].bobot[1] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text5 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[1].bobot[3] = 1/6
          this.kriteria[3].bobot[1] = 6
        }
        if(val == 5) {
          this.kriteria[1].bobot[3] = 1/5
          this.kriteria[3].bobot[1] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text5 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[1].bobot[3] = 1/4
          this.kriteria[3].bobot[1] = 4
        }
        if(val == 7) {
          this.kriteria[1].bobot[3] = 1/3
          this.kriteria[3].bobot[1] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text5 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[1].bobot[3] = 1/2
          this.kriteria[3].bobot[1] = 2
        }
        if(val == 9) {
          this.kriteria[1].bobot[3] = 1
        }
        if(val == 10) {
          this.kriteria[1].bobot[3] = 2
          this.kriteria[3].bobot[1] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text5 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[1].bobot[3] = 3
          this.kriteria[3].bobot[1] = 1/3
        }
        if(val == 12) {
          this.kriteria[1].bobot[3] = 4
          this.kriteria[3].bobot[1] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text5 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[1].bobot[3] = 5
          this.kriteria[3].bobot[1] = 1/5
        }
        if(val == 14) {
          this.kriteria[1].bobot[3] = 6
          this.kriteria[3].bobot[1] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text5 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[1].bobot[3] = 7
          this.kriteria[3].bobot[1] = 1/7
        }
        if(val == 16) {
          this.kriteria[1].bobot[3] = 8
          this.kriteria[3].bobot[1] = 1/8
        }
      }
      if(val == 17) {
        this.text5 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[1].bobot[3] = 9
          this.kriteria[3].bobot[1] = 1/9
        }
      } 
    },
      test6: function(val) {
      if(val == 1) {
        this.text7 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[1].bobot[4] = 1/9
        this.kriteria[4].bobot[1] = 9
      }
      if(val == 3 || val == 2) {
        this.text7 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[1].bobot[4] = 1/8
          this.kriteria[4].bobot[1] = 8
        }
        if(val == 3) {
          this.kriteria[1].bobot[4] = 1/7
          this.kriteria[4].bobot[1] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text7 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[1].bobot[4] = 1/6
          this.kriteria[4].bobot[1] = 6
        }
        if(val == 5) {
          this.kriteria[1].bobot[4] = 1/5
          this.kriteria[4].bobot[1] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text7 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[1].bobot[4] = 1/4
          this.kriteria[4].bobot[1] = 4
        }
        if(val == 7) {
          this.kriteria[1].bobot[4] = 1/3
          this.kriteria[4].bobot[1] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text7 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[1].bobot[4] = 1/2
          this.kriteria[4].bobot[1] = 2
        }
        if(val == 9) {
          this.kriteria[1].bobot[4] = 1
        }
        if(val == 10) {
          this.kriteria[1].bobot[4] = 2
          this.kriteria[4].bobot[1] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text7 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[1].bobot[4] = 3
          this.kriteria[4].bobot[1] = 1/3
        }
        if(val == 12) {
          this.kriteria[1].bobot[4] = 4
          this.kriteria[4].bobot[1] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text7 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[1].bobot[4] = 5
          this.kriteria[4].bobot[1] = 1/5
        }
        if(val == 14) {
          this.kriteria[1].bobot[4] = 6
          this.kriteria[4].bobot[1] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text7 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[1].bobot[4] = 7
          this.kriteria[4].bobot[1] = 1/7
        }
        if(val == 16) {
          this.kriteria[1].bobot[4] = 8
          this.kriteria[4].bobot[1] = 1/8
        }
      }
      if(val == 17) {
        this.text7 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[1].bobot[4] = 9
          this.kriteria[4].bobot[1] = 1/9
        }
      } 
    },
      test7: function(val) {
      if(val == 1) {
        this.text6 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[2].bobot[3] = 1/9
        this.kriteria[3].bobot[2] = 9
      }
      if(val == 3 || val == 2) {
        this.text6 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[2].bobot[3] = 1/8
          this.kriteria[3].bobot[2] = 8
        }
        if(val == 3) {
          this.kriteria[2].bobot[3] = 1/7
          this.kriteria[3].bobot[2] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text6 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[2].bobot[3] = 1/6
          this.kriteria[3].bobot[2] = 6
        }
        if(val == 5) {
          this.kriteria[2].bobot[3] = 1/5
          this.kriteria[3].bobot[2] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text6 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[2].bobot[3] = 1/4
          this.kriteria[3].bobot[2] = 4
        }
        if(val == 7) {
          this.kriteria[2].bobot[3] = 1/3
          this.kriteria[3].bobot[2] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text6 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[2].bobot[3] = 1/2
          this.kriteria[3].bobot[2] = 2
        }
        if(val == 9) {
          this.kriteria[2].bobot[3] = 1
        }
        if(val == 10) {
          this.kriteria[2].bobot[3] = 2
          this.kriteria[3].bobot[2] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text6 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[2].bobot[3] = 3
          this.kriteria[3].bobot[2] = 1/3
        }
        if(val == 12) {
          this.kriteria[2].bobot[3] = 4
          this.kriteria[3].bobot[2] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text6 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[2].bobot[3] = 5
          this.kriteria[3].bobot[2] = 1/5
        }
        if(val == 14) {
          this.kriteria[2].bobot[3] = 6
          this.kriteria[3].bobot[2] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text6 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[2].bobot[3] = 7
          this.kriteria[3].bobot[2] = 1/7
        }
        if(val == 16) {
          this.kriteria[2].bobot[3] = 8
          this.kriteria[3].bobot[2] = 1/8
        }
      }
      if(val == 17) {
        this.text6 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[2].bobot[3] = 9
          this.kriteria[3].bobot[2] = 1/9
        }
      } 
    },
      test8: function(val) {
      if(val == 1) {
        this.text8 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[2].bobot[4] = 1/9
        this.kriteria[4].bobot[2] = 9
      }
      if(val == 3 || val == 2) {
        this.text8 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[2].bobot[4] = 1/8
          this.kriteria[4].bobot[2] = 8
        }
        if(val == 3) {
          this.kriteria[2].bobot[4] = 1/7
          this.kriteria[4].bobot[2] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text8 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[2].bobot[4] = 1/6
          this.kriteria[4].bobot[2] = 6
        }
        if(val == 5) {
          this.kriteria[2].bobot[4] = 1/5
          this.kriteria[4].bobot[2] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text8 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[2].bobot[4] = 1/4
          this.kriteria[4].bobot[2] = 4
        }
        if(val == 7) {
          this.kriteria[2].bobot[4] = 1/3
          this.kriteria[4].bobot[2] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text8 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[2].bobot[4] = 1/2
          this.kriteria[4].bobot[2] = 2
        }
        if(val == 9) {
          this.kriteria[2].bobot[4] = 1
        }
        if(val == 10) {
          this.kriteria[2].bobot[4] = 2
          this.kriteria[4].bobot[2] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text8 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[2].bobot[4] = 3
          this.kriteria[4].bobot[2] = 1/3
        }
        if(val == 12) {
          this.kriteria[2].bobot[4] = 4
          this.kriteria[4].bobot[2] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text8 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[2].bobot[4] = 5
          this.kriteria[4].bobot[2] = 1/5
        }
        if(val == 14) {
          this.kriteria[2].bobot[4] = 6
          this.kriteria[4].bobot[2] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text8 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[2].bobot[4] = 7
          this.kriteria[4].bobot[2] = 1/7
        }
        if(val == 16) {
          this.kriteria[2].bobot[4] = 8
          this.kriteria[4].bobot[2] = 1/8
        }
      }
      if(val == 17) {
        this.text8 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[2].bobot[4] = 9
          this.kriteria[4].bobot[2] = 1/9
        }
      } 
    },
      test9: function(val) {
      if(val == 1) {
        this.text9 = "Mutlak Tidak Lebih Penting dari"
        this.kriteria[3].bobot[4] = 1/9
        this.kriteria[4].bobot[3] = 9
      }
      if(val == 3 || val == 2) {
        this.text9 = "Sangat Tidak Lebih Penting dari"
        if(val == 2) {
          this.kriteria[3].bobot[4] = 1/8
          this.kriteria[4].bobot[3] = 8
        }
        if(val == 3) {
          this.kriteria[3].bobot[4] = 1/7
          this.kriteria[4].bobot[3] = 7
        }
      }
      if(val == 5 || val == 4) {
        this.text9 = "Tidak Lebih Penting dari"
        if(val == 4) {
          this.kriteria[3].bobot[4] = 1/6
          this.kriteria[4].bobot[3] = 6
        }
        if(val == 5) {
          this.kriteria[3].bobot[4] = 1/5
          this.kriteria[4].bobot[3] = 5
        }
      }
      if(val == 7 || val == 6) {
        this.text9 = "Sedikit Tidak Lebih Penting dari"
        if(val == 6) {
          this.kriteria[3].bobot[4] = 1/4
          this.kriteria[4].bobot[3] = 4
        }
        if(val == 7) {
          this.kriteria[3].bobot[4] = 1/3
          this.kriteria[4].bobot[3] = 3
        }
      }
      if(val == 9 || val == 8 || val == 10) {
        this.text9 = "Sama Pentingnya"
        if(val == 8) {
          this.kriteria[3].bobot[4] = 1/2
          this.kriteria[4].bobot[3] = 2
        }
        if(val == 9) {
          this.kriteria[3].bobot[4] = 1
        }
        if(val == 10) {
          this.kriteria[3].bobot[4] = 2
          this.kriteria[4].bobot[3] = 1/2
        }
      }
      if(val == 11 || val == 12) {
        this.text9 = "Sedikit Lebih Penting dari"
        if(val == 11) {
          this.kriteria[3].bobot[4] = 3
          this.kriteria[4].bobot[3] = 1/3
        }
        if(val == 12) {
          this.kriteria[3].bobot[4] = 4
          this.kriteria[4].bobot[3] = 1/4
        }
      }
      if(val == 13 || val == 14) {
        this.text9 = "Lebih Penting dari"
        if(val == 13) {
          this.kriteria[3].bobot[4] = 5
          this.kriteria[4].bobot[3] = 1/5
        }
        if(val == 14) {
          this.kriteria[3].bobot[4] = 6
          this.kriteria[4].bobot[3] = 1/6
        }
      }
      if(val == 15 || val == 16) {
        this.text9 = "Sangat Lebih Penting dari"
        if(val == 15) {
          this.kriteria[3].bobot[4] = 7
          this.kriteria[4].bobot[3] = 1/7
        }
        if(val == 16) {
          this.kriteria[3].bobot[4] = 8
          this.kriteria[4].bobot[3] = 1/8
        }
      }
      if(val == 17) {
        this.text9 = "Mutlak Lebih Penting dari"
        if(val == 17) {
          this.kriteria[3].bobot[4] = 9
          this.kriteria[4].bobot[3] = 1/9
        }
      } 
    },
    },
    computed: {
      eigenMax: function() {
        let em = []
        const reducer = (previous, current) => previous + current
        for(let i=0; i<this.kriteria.length;i++) {
                em.push(this.kriteria[i].eigen)
            }
            return em.reduce(reducer)/this.kriteria.length
      },
      consistencyIndex: function() {
            return (this.eigenMax-this.kriteria.length)/(this.kriteria.length-1)
      },
      consistencyRatio: function() {
          return this.consistencyIndex/1.12
      },
      consistent: function() {
          return (this.consistencyRatio<=0.1)? "Sudah Konsisten" : "Belum Konsisten"
      }
    },
    methods: {
      test: function() {
        this.$emit('switch', this.kriteria)
      }
    }
}
</script>

<style scoped>
.model {
    position: absolute; 
    z-index: 1;
    left: 0;
    top: 0;
    width: 100%; 
    height: 100%;
    overflow: auto;
    background-color: rgba(0,0,0,0.7); 
}
</style>