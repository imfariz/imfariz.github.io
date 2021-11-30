<template>
    <div class="model-crt">
        <div class="model-crt-content ms-auto d-flex flex-column justify-content-center">
            <div class="model-content-title">
                <h5>CRITERIA</h5>
                <p class="mt-3">Input alternatives score here. Click the <br> numbers to edit the alternative’s score</p>
            </div>
            <div class="model-crt-table mt-5">
                <table class="text-center">
                    <thead>
                        <th class="text-start">Criteria</th>
                        <th>Logika Matematika</th>
                        <th>Bahasa Inggris</th>
                        <th>Komputer</th>
                        <th>Wawancara</th>
                        <th>Pengetahuan Umum</th>
                    </thead>
                    <tbody>
                        <tr>
                            <td class="text-start">Logika Matematika</td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                        </tr>
                        <tr>
                            <td class="text-start">Bahasa Inggris</td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                        </tr>
                        <tr>
                            <td class="text-start">Komputer</td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                        </tr>
                        <tr>
                            <td class="text-start">Wawancara</td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                        </tr>
                        <tr>
                            <td class="text-start">Pengetahuan Umum</td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                            <td><input type="number" style="text-align: center" value="2"></td>
                        </tr>
                    </tbody>
                </table>
            </div>
            <div class="model-crt-cta mt-5 align-self-end me-5">
                <button class="cta cta-primary">SAVE</button>
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
    name: 'ModalCriteria',
    components: {
        Icon
    },
}
</script>

<style scoped>
</style>