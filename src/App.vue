<template>
  <div id="app">
    <div class="container">
      <div class="left-menu">
        <div>
          <label for="backgroundColor">Color de fondo:</label>
          <select id="backgroundColor" v-model="selectedBackgroundColor">
            <option v-for="color in colors" :value="color" :key="color">{{ color }}</option>
          </select>
        </div>
        <div>
          <label for="textColor">Color de texto:</label>
          <select id="textColor" v-model="selectedTextColor">
            <option v-for="color in colors" :value="color" :key="color">{{ color }}</option>
          </select>
        </div>
        <div>
          <label>
            <input type="checkbox" v-model="showText"> Mostrar texto
          </label>
        </div>
        <div>
          <label for="borderSize">Borde:</label>
          <input type="range" id="borderSize" min="0" max="100" v-model="borderSize">
        </div>
        <div>
          <label for="textContent">Contenido Textual:</label>
          <textarea id="textContent" v-model="textContent"></textarea>
        </div>
        <div>
          <label for="fontFamily">Tipografía:</label>
          <select id="fontFamily" v-model="selectedFontFamily">
            <option v-for="font in fonts" :value="font" :key="font">{{ font }}</option>
          </select>
        </div>
        <div>
          <label>
            <input type="checkbox" v-model="isOpaque"> Opaco
          </label>
        </div>
        <div>
          <label>
            <input type="radio" v-model="textSize" value="large"> Tamaño de Letra - Grande
          </label>
        </div>
        <div>
          <label>
            <input type="radio" v-model="textSize" value="medium"> Tamaño de Letra - Mediano
          </label>
        </div>
        <div>
          <label>
            <input type="radio" v-model="textSize" value="small"> Tamaño de Letra - Pequeño
          </label>
        </div>
      </div>
      <div class="right-content" :style="{
        backgroundColor: selectedBackgroundColor,
        color: selectedTextColor,
        borderRadius: borderSize === 0 ? '0' : `${Math.min(borderSize / 2, 500)}px`,
        fontFamily: selectedFontFamily,
        textShadow: isOpaque ? '2px 2px 5px rgba(0, 0, 0, 0.5)' : 'none',
        fontSize: textSize === 'large' ? '50px' : (textSize === 'medium' ? '30px' : '14px')
      }" v-show="showText">
        {{ textContent }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      colors: ['red', 'blue', 'green', 'yellow', 'purple'],
      fonts: ['Arial', 'Helvetica', 'Times New Roman', 'Courier New', 'Verdana'],
      selectedBackgroundColor: 'white',
      selectedTextColor: '',
      showText: true,
      borderSize: 0,
      textContent: '',
      selectedFontFamily: 'Arial',
      isOpaque: false,
      textSize: 'medium'
    };
  }
};
</script>

<style>
.container {
  display: flex;
}

.left-menu {
  max-width: 200px;
  padding: 20px;
  max-height: auto;
  background-color: rgb(218, 190, 245)
}

.right-content {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
