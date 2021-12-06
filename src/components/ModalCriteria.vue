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
                        <th v-for="x in bobot" :key="x" v-text="x.nama"></th>
                    </thead>
                    <tbody>
                        <tr v-for="x in bobot" :key="x">
                            <td class="text-start" v-text="x.nama"></td>
                            <td v-for="(y, index) in x.bobot" :key="y"><input type="number" style="text-align: center" v-model="x.bobot[index]"></td>
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
    props: ['bobot']
}
</script>

<style scoped>
</style>