<template>
    <div>
        <div id="timerAdd">
            <label for="timeritle">タイトル</label>
            <input type="text" id="timerTitle" v-model="title">
            <p><input type="number" v-model="hour" max=99 min=0> 時間 : <input type="number" v-model="minute" max=59 min=0> 分 : <input type="number" v-model="second" max=59 min=0> 秒</p>
            
            <button @click="addTimer">タイマーを追加</button>
            <p></p>
        </div>
        <hr>
        <TimerBox v-for="(TimerData, index) in TimerDatas" @delete="timerDelete(index)" :key="index" :TimerData="TimerData">
        </TimerBox>
    </div>
</template>

<script>
import TimerBox from './Timer-box'

export default {
    components:{
        TimerBox
    },
    data() {
        return {
            title:"無題タイマー",
            hour:0,
            minute:0,
            second:0,
            TimerDatas: []
        }
    },
    methods: {
        timerDelete(index) {
            this.TimerDatas.splice(index, 1);
        },
        addTimer() {
            var ResidueSecond = Number((this.hour * 3600) + (this.minute * 60) + Number(this.second))
            this.TimerDatas.push({
                Title:this.title,
                ResidueSecond: ResidueSecond
            })
            this.title = "無題タイマー"
            this.hour = 0
            this.minute = 0
            this.second = 0
        }
    }
}
</script>

<style scoped>

</style>