<template>
  <div class="calculadora">
    <h2>Calculadora Aritmética</h2>

    <div>
      <label for="numero1">Número 1:</label>
      <input type="number" v-model.number="numero1" @input="calcularResultado">
    </div>

    <div>
      <label for="numero2">Número 2:</label>
      <input type="number" v-model.number="numero2" @input="calcularResultado">
    </div>

    <div>
      <label for="operacao">Operação:</label>
      <select v-model="operacao" @change="calcularResultado">
        <option value="+">+</option>
        <option value="-">-</option>
        <option value="*">x</option>
        <option value="/">/</option>
      </select>
    </div>

    <div>
      <label for="resultado">Resultado:</label>
      <input type="text" :value="resultado" disabled>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: '+',
      resultado: 0
    };
  },
  methods: {
    calcularResultado() {
      switch (this.operacao) {
        case '+':
          this.resultado = this.numero1 + this.numero2;
          break;
        case '-':
          this.resultado = this.numero1 - this.numero2;
          break;
        case '*':
          this.resultado = this.numero1 * this.numero2;
          break;
        case '/':
          this.resultado = this.numero1 / this.numero2;
          break;
        default:
          this.resultado = 0;
      }
    }
  }
};
</script>

<style scoped>
.calculadora {
  max-width: 400px;
  margin: auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.calculadora div {
  margin-bottom: 10px;
}

.calculadora label {
  font-weight: bold;
  display: block;
}

.calculadora input[type="number"],
.calculadora input[type="text"],
.calculadora select {
  width: 100%;
  padding: 8px;
  font-size: 16px;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
}

.calculadora input[type="text"] {
  background-color: #f9f9f9;
  cursor: not-allowed;
}
</style>
