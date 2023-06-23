<script setup>

  import { ref } from 'vue'

function lerMatriz() {
  const matriz = []
  const linhas = parseInt(prompt('Informe o número de linhas da matriz:'))
  const colunas = parseInt(prompt('Informe o número de colunas da matriz:'))

  for (let i = 0; i < linhas; i++) {
    const linha = []

    for (let j = 0; j < colunas; j++) {
      const valor = parseInt(prompt(`Informe o valor para a posição [${i + 1}][${j + 1}]:`))
      linha.push(valor)
    }

    matriz.push(linha)
  }

  return matriz
}

function calcularSomaTraco(matriz) {
  const linhas = matriz.length
  const colunas = matriz[0].length
  if (linhas !== colunas) {
    return 'A matriz deve ser quadrada .'
  } else {
    let soma = 0
    for (let i = 0; i < linhas; i++) {
      soma += matriz[i][i]
    }
    return soma
  }
}

const matriz = lerMatriz()

const somaTraco = calcularSomaTraco(matriz)

const resposta = ref(null)

function mostrarTransposta() {

  if (typeof somaTraco === typeof 1) {
    resposta.value = `O traço da matriz é: ${somaTraco}`
  } else {
    resposta.value = `Erro: ${somaTraco}`
  }
}

mostrarTransposta()
</script>

<template>
  <p>{{ resposta }}</p>
</template>

<style scoped></style>
