<template>
  <q-page class="flex flex-center column">
    <h3 class="q-mb-sm">Calculadora de IMC</h3>
    <p>Calcularemos o seu IMC de acordo com os dados preenchidos.</p>
    <q-card >
      <q-card-section class="flex justify-center column">
          <q-input rounded outlined v-model="peso"  label="Peso" />
            <q-input rounded outlined v-model="altura" class="q-mt-xs" label="Altura" />
             <q-btn style="background: #FF0080; color: white" v-on:click="calculo_IMC" label="Calcular" class="q-mt-md" />
      </q-card-section>
       <q-separator inset />
       <q-card-section class="flex justify-center column">
         <q-chip v-if= "IMC != ''">
        <q-avatar color="red" text-color="white">{{IMC}}</q-avatar>
        {{resultado}}
         </q-chip>
       </q-card-section>
    </q-card>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  methods: {
    calculo_IMC () {
      this.IMC = parseInt(this.peso / (this.altura * this.altura))
    }
  },
  data () {
    return {
      peso: '',
      altura: '',
      IMC: ''
    }
  },
  computed: {
    resultado () {
      if (this.IMC < 16) {
        return 'Subpeso Severo'
      } else if (this.IMC >= 16 && this.IMC <= 19.9) {
        return 'Subpeso'
      } else if (this.IMC >= 20 && this.IMC <= 24.9) {
        return 'Normal'
      } else if (this.IMC >= 25 && this.IMC <= 29.9) {
        return 'Sobrepeso'
      } else if (this.IMC >= 30 && this.IMC <= 39.9) {
        return 'Obeso'
      } else {
        return 'Obeso Mórbido'
      }
    }
  }
}
</script>
