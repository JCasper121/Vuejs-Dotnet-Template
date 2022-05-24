<template>
  <div class="hello">
    <h3>{{msg}}</h3>
  </div>
  <code>
    <pre>
      {{JSON.stringify(forecasts, null, 2)}}
    </pre>
  </code>
</template>

<script lang="ts">
import { Options, Vue } from 'vue-class-component'

@Options({
  props: {
    msg: String
  }
})

export default class HelloWorld extends Vue {
  forecasts?: [] = [];
  msg!: string;

  created () {
    fetch('https://localhost:5001/WeatherForecast')
      .then(function (res) { return res.json() })
      .then((res) => {
        this.forecasts = res
        
      })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
