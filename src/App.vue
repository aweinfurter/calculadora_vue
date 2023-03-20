<script setup>
import { reactive } from 'vue';

const estado = reactive({
  numero1: 0,
  numero2: 0,
  operacao: '+',
  resultado: 0,
})

const resultado = () => {
  const { operacao, numero1, numero2 } = estado

  switch (operacao) {
    case '+':
      estado.resultado = Number(numero1) + Number(numero2)
      break;

    case '-':
      estado.resultado = numero1 - numero2
      break;

    case '*':
      estado.resultado = numero1 * numero2
      break;

    case '/':
      estado.resultado = numero1 / numero2
      break;

    default:
      estado.resultado = 0
  }
}

</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 mt-4 bg-dark rounded-3">
      <h1 class="text-light">Calculadora - VueJs</h1>
      <p class="text-light">
        Tarefa do módulo 27 do curso de front-end da EBAC
      </p>
    </header>
    <form>
    <div class="row">
      <div class="col-2">
        <input class="form-control" type="number" placeholder="0" @input="evento => { estado.numero1 = evento.target.value; resultado(); }">
      </div>
      <div class="col-2">
        <select class="form-select" @change="evento => { estado.operacao = evento.target.value; resultado(); }">
          <option value="+">+</option>
          <option value="-">-</option>
          <option value="*">*</option>
          <option value="/">/</option>
        </select>
      </div>
      <div class="col-2">
        <input class="form-control" type="number" placeholder="0" @input="evento => { estado.numero2 = evento.target.value; resultado(); }">
      </div>
      <div class="col-6">
        <h3>
          Resultado = {{ estado.resultado }}
        </h3>
      </div>
    </div>
  </form>
  </div>
</template>

<style scoped>
.container {
  max-width: 600px;
}
</style>
