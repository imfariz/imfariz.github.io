<template>
    <div class="model-cdt">
            <div class="model-cdt-content px-5 d-flex flex-column justify-content-center">
                <div class="model-content-title">
                    <h5>CANDIDATES</h5>
                    <p class="mt-3">Input candidate score here. Click the <br> numbers to edit the candidate’s score</p>
                </div>
                <div class="model-cdt-table mt-5">
                    <table class="w-100 text-center">
                        <thead>
                            <th class="text-start" style="width: 25%">Alternatives</th>
                            <th>Logika Matematika</th>
                            <th>Bahasa Inggris</th>
                            <th>Komputer</th>
                            <th>Wawancara</th>
                            <th>Pengetahuan Umum</th>
                        </thead>
                        <tbody>
                            <tr v-for="alt in alternatives" :key="alt">
                                <td class="text-start" v-text="alt.nama"></td>
                                <td><input type="number" style="text-align: center" v-model="alt.logma"></td>
                                <td><input type="number" style="text-align: center" v-model="alt.english"></td>
                                <td><input type="number" style="text-align: center" v-model="alt.computer"></td>
                                <td><input type="number" style="text-align: center" v-model="alt.interview"></td>
                                <td><input type="number" style="text-align: center" v-model="alt.general"></td>
                            </tr>
                        </tbody>
                    </table>
                </div>
                <div class="model-cdt-cta mt-5 align-self-end me-5">
                    <button class="cta cta-primary" @click="save">SAVE</button>
                </div>
            </div>
            <button class="close" @click="$emit('checked')">
                <Icon icon="eva:arrow-ios-back-outline" style="font-size:40px" />
            </button>
    </div>
</template>

<script>
import {Icon} from '@iconify/vue'

export default {
    name: 'ModalAlternative',
    components: {
        Icon
    },
    props: {
        alt: Array
    },
    created() {
        this.alternatives = this.alt
    },
    data() {
        return {
            alternatives: []
        }
    },
    methods: {
        save: function() {
            this.$emit('switch', this.alternatives)
            this.$emit('checked')
        }
    }
}
</script>

<style scoped>
</style>