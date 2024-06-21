<template>
    <ul class="row">
        <li class="col-m">{{ time.nomeTime}}</li>
        <li class="col-l">{{ time.posicao}}</li>
        <li class="col-l">{{ time.pontos}}</li>
        <li class="col-l">{{ time.gols}}</li>
        <li class="col-m">{{ time.campeonato}}</li>
        <li class="col-l">{{ time.vitorias}}</li>
        <li class="col-m">{{ time.derrotas}}</li>
      </ul>
</template>

<script>
export default {
    name: 'RowLocal',
    props:{
        time:{
            type: Object,
            required: true
        }
    }
}
</script>

<style>

</style>