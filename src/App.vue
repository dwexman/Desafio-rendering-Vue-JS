<template>
  <div class="container">
    <!-- Controls -->
    <div class="controls">
      <label>Color de fondo</label>
      <input type="color" v-model="bgColor" />

      <label>Color de texto</label>
      <input type="color" v-model="textColor" />

      <label>
        <input type="checkbox" v-model="showText" />
        Mostrar texto
      </label>

      <label>Borde</label>
      <input type="range" v-model="borderRadius" min="0" max="50" />

      <label>Contenido textual</label>
      <input type="text" v-model="content" />

      <label>Tipografía</label>
      <select v-model="fontFamily">
        <option v-for="font in fonts" :key="font" :value="font">{{ font }}</option>
      </select>

      <label>Opaco</label>
      <input type="checkbox" v-model="opacity" />

      <label>Tamaño de letra</label>
      <div>
        <input type="radio" value="small" v-model="fontSize" /> Pequeño
        <input type="radio" value="medium" v-model="fontSize" /> Mediano
        <input type="radio" value="large" v-model="fontSize" /> Grande
      </div>
    </div>

    <!-- Figura a la derecha -->
    <div v-show="showFigure"
         class="figure"
         :style="{
           backgroundColor: bgColor,
           color: textColor,
           borderRadius: borderRadius === 50 ? '50%' : borderRadius + 'px',
           fontFamily: fontFamily,
           opacity: opacity ? 0.5 : 1
         }"
         :class="[fontSize]">
      <span v-if="showText">{{ content }}</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      bgColor: "#8bc34a",   
      textColor: "#ffffff", 
      borderRadius: 25,     
      content: "Denise Wexman", 
      fontFamily: "Cursive",     
      opacity: false,       
      fontSize: "medium",   
      showText: true,      
      showFigure: true,     
      fonts: ["Cursive", "Arial", "Helvetica", "Times New Roman"] 
    };
  }
};
</script>

<style>
.container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px;
}

.controls {
  display: flex;
  flex-direction: column;
  gap: 10px;
  width: 300px;
  background-color: #2f4f4f;
  padding: 20px;
  border-radius: 10px;
  color: white;
}

.figure {
  width: 300px;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #8bc34a;
  color: white;
  margin-left: 50px; 
}

.figure span {
  text-align: center;
}

/* Clases para el tamaño de letra */
.small {
  font-size: 14px;
}

.medium {
  font-size: 28px;
}

.large {
  font-size: 56px;
}
</style>
