<template>

  <section class="container">
    <!-- FORMULARIO -->
    <form class="formulario">

      <label for="">Color de fondo:</label>
      <input v-model="colorFondo" type="text" name="" />
      <label for="">color de texto</label>
      <input v-model="colorTexto" type="text" name="" />
      <label>
        Mostrar texto
        <input v-model="mostrarTexto" type="checkbox" name="" />
      </label>
      <label for="">Borde</label>
      <input v-model="borde" type="range" id="input4" name="input4" min="0" max="200" step="1" />
      <label>Contenido actual</label>
      <input v-model="contenidoTextual" type="text" name="" value="" maxlength="" />

      <fieldset>
        <legend>Tipografía:</legend>
        <select v-model="selectTipoLetra" name="tipografia">
          <option value="" disabled>Selecciona una opcion</option>
          <option v-for="tipografia in tipografiaTexto" :key="tipografia" :value="tipografia">
            {{ tipografia }}
          </option>
        </select>
      </fieldset>

      <label>
        Opaco
        <input v-model="opacidadCuadro" type="checkbox" name="" />
      </label>

      <fieldset>
        <legend>Tamaño de letra</legend>

        <input v-model="tamañoTexto" type="radio" id="pequenio" name="tamano" value="pequeño" />
        <label for="pequeño">Pequeño</label>
        <input v-model="tamañoTexto" type="radio" id="mediano" name="tamano" value="mediano" />
        <label for="mediano">Mediano</label>
        <input v-model="tamañoTexto" type="radio" id="grande" name="tamano" value="grande" />
        <label for="grande">Grande</label>
      </fieldset>
    </form>

    <!-- CUADRO DINAMICO -->
     
    <div class="cuadroDinamico"
      :style="{ backgroundColor: colorFondo, color: colorTexto, fontFamily: selectTipoLetra, borderRadius: borde + 'px', }"
      :class="{
        opacidad: opacidadCuadro === true,
        textoPequeño: tamañoTexto === 'pequeño',
        textoMediano: tamañoTexto === 'mediano',
        textoGrande: tamañoTexto === 'grande',
      }">
      <h1 v-if="mostrarTexto">{{ contenidoTextual }}</h1>
    </div>
  </section>
  
</template>

<script>
export default {
  name: "formularioInteractivo",
  data() {
    return {
      colorFondo: "",
      colorTexto: "",
      mostrarTexto: "",
      selectTipoLetra: "",
      borde: 0,
      contenidoTextual: "",
      tipografiaTexto: [
        "Impact",
        "Brush Script MT",
        "Georgia",
        "Garamond",
      ],
      opacidadCuadro: false,
      tamañoTexto: "",
    };
  },
};
</script>

<style>

.container {
  margin: 50px;
  display: flex;
  justify-content: space-around;
  align-items: center;
}

.formulario {
  display: flex;
  flex-direction: column;
  padding: 25px;
  width: 25%;
  border-radius: 20px;
  box-shadow: 5px 5px 5px gray;
  background-color: rgb(63, 110, 112);
}

label {
  padding: 12px 0;
}

fieldeset{
  padding: 15px 0;
}

.cuadroDinamico {
  width: 400px;
  height: 400px;
  box-shadow: 5px 5px 5px gray;
  border: solid 1px rgba(0, 0, 0, 0.21);
  text-align: center;
  overflow: hidden;
  word-wrap: break-word;
  white-space: pre-wrap;
}



.opacidad {
  opacity: 0.5;
}

.textoPequeño {
  font-size: 12px;
}

.textoMediano {
  font-size: 18px;
}

.textoGrande {
  font-size: 24px;
}
</style>
