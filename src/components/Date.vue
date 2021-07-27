<template>
  <div class="main">
    <span class="text">还剩</span>
    <span class="time">{{meet.day}}天{{meet.hour}}时{{meet.minute}}分{{meet.second}}秒</span>
    <span>可以见面</span>
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
      timer:null
    }
  },
  mounted() {
    this.do()
  },
  methods:{
    do(){
      this.timer&&clearTimeout(this.timer)
      const date=Date.parse('2021-08-20 22:00:00')
      const now=Date.now();
      let duration=date-now
      if (duration<0)return;
      this.meet=this.durationFormatter(duration);
      this.timer=setTimeout(()=>{this.do()},1000)
    },
    durationFormatter(time) {
      if (!time) return { ss: 0 };
      let t = time;
      const ms = t % 1000;
      t = (t - ms ) / 1000;
      const ss = t % 60;
      t = (t - ss) / 60;
      if (t < 1) return { ss };
      const mm = t % 60;
      t = (t - mm) / 60;
      if (t < 1) return { mm, ss };
      const hh = t % 24;
      t = (t - hh) / 24;
      if (t < 1) return { hh, mm, ss };
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