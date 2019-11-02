<template>
    <div>
        <p>{{TimerData.Title}}:{{TimerData.ResidueSecond}}</p>
        <p>{{Hour}}:{{Minute}}:{{Second}}</p>
        <button @click="$emit('delete')">取り消し</button>
    </div>
</template>

<script>
export default {
    props: {
        TimerData: {
            Title: String,
            ResidueSecond: Number
        }
    },
    computed: {
        Hour() {
            return Math.floor(this.TimerData.ResidueSecond / 3600)
        },
        Minute() {
            return Math.floor(this.TimerData.ResidueSecond / 60) % 60
        },
        Second() {
            return Math.floor(this.TimerData.ResidueSecond % 60)
        }
    },
    methods: {
    },
    created() {
        var countDownInterval = setInterval(() => {
            if (this.TimerData.ResidueSecond <= 0) {
                clearInterval(countDownInterval);
                alert(this.TimerData.Title+ "が終了しました")
                this.$emit('delete')
            }
            this.TimerData.ResidueSecond -= 1;
        }, 1000)
    }
}
</script>