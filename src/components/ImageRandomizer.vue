<template>
  <q-page class="flex flex-center">
    <div class="row">
      <div class="col">
        <img
          alt="Imagem feliz"
          :src="urlsComputed"
          style="width: 300px; height: auto"
        />
        <div class="row">
          <div class="col-5">
            <q-btn
              color="amber"
              class="full-width"
              :onclick="() => getImageUrl()"
              label="Gerar imagem"
              flat="true"
            />
          </div>
          <div class="col-2"></div>
          <div class="col-5">
            <q-btn
              color="purple"
              class="full-width"
              :onclick="() => getImageUrl()"
              label="Compartilhar"
              flat="true"
            />
          </div>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup>
import { ref, computed } from "vue";

defineOptions({
  name: "ImageRandomizer",
});

const imagesDatabase = [
  "https://i.pinimg.com/564x/aa/d6/9f/aad69faff0761571b238fbd0ae4baa57.jpg",
  "https://www.momentodivino.com.br/img/webp/imagens10/bom-dia-60559x8jFVj3gp.webp",
  "https://cdn.pensador.com/img/imagens/pe/ns/pensador_bom_dia_com_fe_01.jpg?auto_optimize=low&width=655",
  "https://cdn.pensador.com/img/temas/fr/as/frases_de_bom_dia_para_alguem_especial.jpg?class=ogImageWide",
  "https://play-lh.googleusercontent.com/r0xN9hXjVDp3Jy6auZhvByz7HN7PfnikPQAis49N3rMoltG1VT_z_iZPr9GHJQ5r9zg",
  "https://cdn.pensador.com/img/imagens/bo/md/bom_dia_mensagens_de_bom_dia_f_l.jpg?class=ogImageSquare",
  "https://i.pinimg.com/236x/ee/f7/80/eef7807fbbf4ffda0e0b7cc5b4d96af2.jpg",
  "https://cdn.pensador.com/img/imagens/me/ns/mensagens_e_frases_de_boa_noite_para_compartilhar_f_l.jpg?class=ogImageSquare",
  "https://www.42frases.com.br/wp-content/uploads/2023/08/boa-noite-que-os-anjos.png",
  "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRijR7iVMwOd6BddtGcNWvHjr_gDmxhDHVJ3LnThA8948KtpRi5UPMRwCm-xG2ZofeWX6g&usqp=CAU",
  "https://www.momentodivino.com.br/img/imagens3/boa-noite-195330csMxgxws.jpg",
  "https://cdn.pensador.com/img/imagens/me/ns/mensagens_de_paz_11.jpg?auto_optimize=low&width=655",
  "https://i.pinimg.com/736x/0e/78/06/0e7806c78f7765b2aa85c2038b35fb0f.jpg",
  "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTKePXy0zQj8RZJ2JzORdNqufWqAe8zbKi9Ig&usqp=CAU",
  "https://i.pinimg.com/564x/a8/2b/1c/a82b1ca49671b3f73be02d641636bc08.jpg",
  "https://imagens.net.br/wp-content/webp-express/webp-images/doc-root/wp-content/uploads/2023/08/uma-colecao-de-imagens-de-boa-tarde-para-encantar-seu-dia-0.jpg.webp",
  "https://play-lh.googleusercontent.com/FNIcUznGNXxkRMgExPHWbKjzFVvX4jLm9r_3RIWOefGVz4B_dLV5Z0a85w-MvvifZio=w526-h296-rw",
  "https://i.pinimg.com/564x/70/59/bf/7059bfb595bd13ad9177cfd13f1fdde8.jpg",
  "https://img.elo7.com.br/product/600x380/4DB0CEF/jogo-de-6-placas-setas-jardim-paz-amor-alegria-gratidao-placas.jpg",
  "https://cdn.pensador.com/img/frase/jo/ha/johann_goethe_a_alegria_nao_esta_nas_coisas_esta_em_nos_l2p3m4k.jpg",
  "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSO_XJRF5di-D1YP3kkhscmtEhcNKy7dZ05rw&usqp=CAU",
  "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSvmUytwUFX2NoDNtYa-H7r3Ks6Yth7gw7VnQ&usqp=CAU",
];

const imagesUrl = ref("Urls");
imagesUrl.value = imagesDatabase[getRandomInt(imagesDatabase.length)];

const urlsComputed = computed({
  // getter
  get() {
    return imagesUrl.value;
  },
  // setter
  set() {
    imagesUrl.value = getImageUrl();
  },
});

const getImageUrl = () => {
  const randomInt = getRandomInt(imagesDatabase.length);
  imagesUrl.value = imagesDatabase[randomInt];
};

function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}
</script>
