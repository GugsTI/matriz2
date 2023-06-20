<template>
  <div class="matrix-container">
    <h3>Matriz:</h3>
    <table class="matrix-table">
      <tr v-for="(linha, indexLinha) in matriz" :key="indexLinha">
        <td v-for="(valor, indexColuna) in linha" :key="indexColuna">
          {{ valor }}
        </td>
      </tr>
    </table>

    <h3>Vetor de maiores elementos:</h3>
    <ul class="vector-list">
      <li v-for="(elemento, index) in vetorMaioresElementos" :key="index">
        {{ elemento }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      matriz: [[1, -2, 3], [4, 5, -6], [7, -8, 9]],
      vetorMaioresElementos: [],
    };
  },
  function() {
    this.encontrarMaioresElementos();
  },
  methods: {
    encontrarMaioresElementos() {
      const colunas = this.matriz[0].length;

      for (let j = 0; j < colunas; j++) {
        let maiorElemento = Number.MIN_SAFE_INTEGER;
        for (let i = 0; i < this.matriz.length; i++) {
          const elementoAtual = Math.abs(this.matriz[i][j]);
          if (elementoAtual > maiorElemento) {
            maiorElemento = elementoAtual;
          }
        }
        this.vetorMaioresElementos.push(maiorElemento);
      }
    },
  },
};
</script>