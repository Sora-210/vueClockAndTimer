<template>
    <div id="clock">
        <p> 現在時刻 </p>
        <div id="time">
            <span>{{ time }}</span>
        </div>
    </div>
</template>

<script>
const zero = (num) => {
    if (String(num).length === 1) {
        return '0' + num
    }
    return num
}
export default {
    created() {
        setInterval(() => {
            var date = new Date()
            this.hour = date.getHours()
            this.minite = date.getMinutes()
            this.second = date.getSeconds()
        }, 1000)
    },
    data () {
        return {
            hour:0,
            minite:0,
            second: 0
        }
    },
    computed: {
        time() {
            return zero(this.hour) + ' : ' + zero(this.minite) + ' : ' + zero(this.second);
        }
    }
}
</script>

<style scoped>
#clock {
    margin: 0;
    padding: 0;
    padding: 15px 0px;
}

#clock p {
    margin: 5px 0px;
    font-size: 30px;
}

#time {
    font-size: 70px;
    font-weight: bold;
    font-family: lcdphone;
}
</style>