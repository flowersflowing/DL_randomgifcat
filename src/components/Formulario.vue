<template>
  <div class="formulario">
    <form @submit="armarGif()">
      <div class="espacio">
        <label for="titulo">Título</label>
        <input type="text" v-model="titulo" placeholder="Miau">      
      </div>
      <div class="espacio">
        <label for="filtro">Filtro</label>
        <select name="filtros" id="filtros" v-model="filtro">
          <option value="sepia">sepia</option>
          <option value="blanconegro">blur</option>
          <option value="sinfiltro">pixel</option>
        </select>    
      </div>
      <div class="espacio">
        <label for="colores">Color</label>
        <select name="colores" id="colores" v-model="color">
          <option value="red">rojo</option>
          <option value="blue">azul</option>
          <option value="green">verde</option>
          <option value="white">blanco</option>
          <option value="yellow">amarillo</option>
        </select>
        <span id="pelota" :style="{backgroundColor: this.color}"></span>
      </div>
      <div class="espacio">
        <label for="tamano">Tamaño</label>
        <input type="text" placeholder="300" v-model="tamano">      
      </div>
      <button type="submit">Obtener mi gif de gatito</button>
    </form>
    <div class="resultado">
      <img :src="imagen" alt="">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Formulario',
  data() {
    return {
      titulo: '',
      filtro: '',
      color: '',
      tamano: '',
      imagen: '',
    }
  },
  methods: {
    armarGif() {
      fetch(`https://cataas.com/cat/gif/says/${this.titulo}?filter=${this.filtro}&color=${this.color}&size=${this.tamano}`)
      .then(result => {
        this.imagen = result.url;
      })
    }
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.espacio {
  padding-top: 1em;
}
form {
  margin: 0;
  background-color: rgb(245, 184, 184);
}
button {
  margin: 3em;
}
#pelota {
  height: 20px;
  width: 20px;
  border-radius: 50%;
  display: inline-block;
}
.resultado {
  background-color: #a5d9f1;
  padding-top: 100px;
  padding-bottom: 200px;
}
</style>
