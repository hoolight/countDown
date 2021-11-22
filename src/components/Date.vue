<template>
  <div class="main">
    <div v-if="showTime">
      <span class="text">还剩</span>
      <span class="time">{{meet.day?meet.day+'天':''}}{{meet.hour?meet.hour+'时':''}}{{meet.minute?meet.minute+'分':''}}{{meet.second?meet.second+'秒':''}}</span>
      <span>可以见面</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "date",
  data(){
    return {
      meet:{
        day:'',
        hour:'',
        minute:'',
        second:''
      },
      showTime:true,
      timer:null
    }
  },
  mounted() {
    this.do()
  },
  methods:{
    do(){
      this.timer&&clearTimeout(this.timer)
      const date=Date.parse('2021-09-18T22:30:00')
      const now=Date.now();
      let duration=date-now
      if (duration<0){
        this.showTime = false
        return;
      }
      this.meet=this.durationFormatter(duration);
      this.timer=setTimeout(()=>{this.do()},1000)
    },
    durationFormatter(time) {
      if (!time) return { second:0 };
      let t = time;
      const ms = t % 1000;
      t = (t - ms ) / 1000;
      const ss = t % 60;
      t = (t - ss) / 60;
      if (t < 1) return {  second:ss };
      const mm = t % 60;
      t = (t - mm) / 60;
      if (t < 1) return { minute:mm, second:ss };
      const hh = t % 24;
      t = (t - hh) / 24;
      if (t < 1) return { hour:hh, minute:mm, second:ss };
      const dd = t;
      return { day:dd, hour:hh, minute:mm, second:ss };
    },
  }
}
</script>

<style scoped>
  .main{
    text-align: center;
  }
  .time{
    color: red;
  }
  .text{
    size: B5;
  }
</style>