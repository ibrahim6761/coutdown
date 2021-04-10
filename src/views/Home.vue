<template>
  <div>
    <h3>Hello World</h3>
    <Counter
    :year="2021"
    :mont="4"
    :date="8"
    :minute="59"
    :second="59"
    :milliesecond="31"
    >

    </Counter>
  </div>
</template>

<script>
import Counter from "@/components/Counter";
export default {
  name : "Home",
  components : {
    Counter : Counter
  }
}
</script>

<style>

</style>