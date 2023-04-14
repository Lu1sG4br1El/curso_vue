<template>
<h2>Hola {{ titulo.toUpperCase() }}</h2>
<br>
<h2 style="color: red;">Gabo</h2>
<ul>
  <template v-for="item in array_Formulas" :key="item.formula">
    <li v-if="item.stock > 0">{{ item.formula }} -> {{ item.monto }} -> {{ item.tiempo }} -> {{ item.pago_inicial }} -> {{ item.pago_final }}</li>
  </template>
</ul>
<h2 style="color: aqua;">Formulas =></h2>
</template>

<script setup>
const titulo = 'esto es mate financiero'
const array_Formulas = [
  {
    formula: "moto de interes simple = costo * (interes * tiempo estipulado)",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  },
  {
    formula: "pago con interes futuro = pago * (interes + int futuro)^n pagos",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  },
  {
    formula: "Pago por interés forma 1 = fuente acumulada / (interés + interés compuesto) ^ n pagos",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  },
  {
    formula: "Pago por interés forma 2 = fuente acumulada * (interés + interés compuesto) * (-n pagos * n pagos)",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  },
  {
    formula: "Tasa efectiva por mes = tasa capital del año / periodo de capitalización",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  },
  {
    formula: "Interés vencido = interés vencido / (periodo vencido - interés vencido)",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  },
  {
    formula: "Interés anticipado = interés anticipado / (periodo anticipado + interés anticipado)",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  },
  {
    formula: "Tasa real = (1ra inversión + inversión inicial) * (1ra inversión + inversión final) – inversión actual",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  },
  {
    formula: "Conjunto de pagos iguales = cuota * (tasa efectiva periódica – (tasa efectiva periódica + cuota) / número de pagos)",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  },
  {
    formula: "Conjunto de pagos periódicos = cuota * ((tasa efectiva periódica / cuota) * (número de pagos periódicos * número periódico sin pagos))",
    monto: 40,
    tiempo: "15 dias",
    pago_inicial: 1000,
    pago_final: 3000,
    stock: 20
  }
]
</script>