<template>
  <div>
      <section class="text-3xl flex justify-center content-center flex-col mx-auto text-center">Buy Now</section>
      <section class="flex text-6xl justify-center content-center">
        <div class="days mr-2 relative">
          {{displayDays}}
          <div class="label text-sm absolute bottom-0">days</div>
        </div>
         <span class="leading-snug">:</span>

        <div class="hours mx-2 relative">
          {{displayHours}}
          <div class="label text-sm absolute bottom-0">hours</div>
        </div>
        <span class="leading-snug">:</span>

        <div class="minutes mx-2 relative">
          {{displayMinutes}}
          <div class="label text-sm absolute bottom-0">Minutes</div>
        </div>
        <span class="leading-snug">:</span>


        <div class="minutes mx-2 relative">
          {{displaySeconds}}
          <div class="seconds text-sm absolute bottom-0">seconds</div>
        </div>
        <span class="leading-snug">:</span>
      </section>
  </div>
</template>

<script>
export default {
  props :['year', 'mont', 'date', 'hour', 'minute', 'second', 'milliesecond'],
  data(){
    return{
      displayDays : 0,
      displayHours : 0,
      displayMinutes: 0,
      displaySeconds :0
    }
  },
  computed : {
    _seconds : () => 1000,
    _minutes(){
      return this._seconds * 60
    },
    _hours(){
      return this._minutes * 60
    },
    _days(){
      return this._hours * 24
    },
    end(){
      return new Date(
        this.year,
        this.mont,
        this.date,
        this.hour,
        this.minute,
        this.second,
        this.milliesecond
      )
    }
  },
  mounted() {
    this.showRemaining()
  },
  methods: {

    formatNum: num => (num <10 ? "0" + num : num),

    showRemaining(){
      const timer = setInterval(() => {
        const now = new Date();
        //const end = new Date(2021, 4, 7, 10,10,10,10)
        const distance = this.end.getTime() - now.getTime()

        if (distance < 0){
          clearInterval(timer);
          return
        }

        const days = Math.floor((distance / this._days));
        const hours = Math.floor((distance % this._days) / this._hours);
        const minutes = Math.floor((distance %  this._hours) / this._minutes);
        const seconds = Math.floor((distance % this._minutes) / this._seconds);
        this.displayMinutes = this.formatNum(minutes)
        this.displaySeconds =  this.formatNum(seconds)
        this.displayHours = this.formatNum(hours)
        this.displayDays = this.formatNum(days)
      })
    }
  }
}
</script>

<style scoped>
.seconds {
  max-width: 60px;
}
</style>