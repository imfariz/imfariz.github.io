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
                        <p>Logika Matematika</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Bahasa Inggris</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Logika Matematika</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Komputer</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Logika Matematika</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Wawancara</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Logika Matematika</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Bahasa Inggris</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Komputer</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Bahasa Inggris</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Wawancara</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Bahasa Inggris</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Komputer</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Komputer</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum</p>
                    </div>
                </div>
                <div class="input-list d-flex justify-content-around align-items-center my-3">
                    <div class="subject">
                        <p>Wawancara</p>
                    </div>
                    <div class="input-slide text-center">
                        <p>Equals to</p>
                        <input type="range" class="sl" name="acs" id="drf">
                    </div>
                    <div class="subject">
                        <p>Pengetahuan Umum</p>
                    </div>
                </div>
            </div>
            <div class="model-cta mt-auto mb-5 align-self-end me-5">
                <button class="cta cta-primary">SAVE</button>
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