<script setup>
const enderecoImagem = 'https://dfstudio-d420.kxcdn.com/wordpress/wp-content/uploads/2019/06/digital_camera_photo-1080x675.jpg';
const nome = 'Andrey Carlos';
const botaoEstaHabilitado = false;
const meuObjeto = {
  nome: 'Andrey',
  filmeFavorito: 'Matrix'
}

function dizOla(nome){
  return `${nome} diz oi`;
}
</script>

<template>
  <!-- <h1>{{ meuObjeto.filmeFavorito }}</h1>; -->
  <h1>{{ dizOla('paula') }}</h1>
  <img :src="enderecoImagem" alt="Imagem">
  <button :disabled="!botaoEstaHabilitado">Enviar mensagem</button>
</template>

<style scoped></style>