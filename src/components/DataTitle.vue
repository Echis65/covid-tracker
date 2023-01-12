<template>
    <div class="text-center ">
        <div class="text-3xl">{{text}}</div>
        <div class="text-2xl mt-4 mb-10  ">{{timeStamp}}</div>
    </div>
</template>


<script>
import moment from 'moment'
export default {
    props:['text', 'dataDate'],
    computed: {
        timeStamp() {
         return moment(this.dataDate).format('Do MMMM Y')
        }
    }
}
</script>