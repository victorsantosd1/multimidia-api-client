<template>
    <ul class="row">
        <li class="col-m" style="border-left-width: 3px; text-align: start;"
          :style="{borderLeftColor: setColor(time.stats[10].value)}">
          {{ time.stats[10].value}}°
          <img :src="time.team.logos[0].href" height="16px"> {{time.team.name}}
        </li>
        <li class="col-l">{{ time.stats[3].value}}</li>
        <li class="col-l">{{ time.stats[0].value}}</li>
        <li class="col-l">{{ time.stats[7].value}}</li>
        <li class="col-l">{{ time.stats[6].value}}</li>
        <li class="col-l">{{ time.stats[1].value}}</li>
        <li class="col-l">{{ time.stats[5].value}}</li>
        <li class="col-l">{{ time.stats[4].value}}</li>
        <li class="col-l">{{ time.stats[2].value}}</li>
      </ul>
</template>

<script>
export default {
    name: 'Row',
    props:{
        time:{
            type: Object,
            required: true
        }
    },
    methods: {
      setColor(position) {
        if (position < 5) {
          return "blue"
        }
        else if (position < 7) {
          return "orange"
        }
        else if (position < 13) {
          return "green"
        }
        else if (position >= 17) {
          return "red"
        }
      }
    }
}
</script>

<style>

</style>