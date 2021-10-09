<template>
  <div class="hero is-medium is-bold">
    <div class="hero-body">
      <div class="container">
        <div class="container__about">
          <h1 class="title">About me:</h1>
          <p class="subtitle">
            Sou graduado no curso de bacharel em Sistema de Informações, pela
            Unigranrio, desde 2017. Fui o segundo melhor na avaliação geral dos
            cursos de tecnologias da faculdade, fruto de toda minha dedicação
            que procuro entregar no aprendizado de novas linguagens e
            tecnologias. Desenvolvedor dedicado com experiência em POO, Java,
            SQL, PHP, JavaScript, CSS, React, Vue, programando diversos tipos de
            aplicações que você pode encontrar abaixo, desde soluções acadêmicas
            até aplicações para freelances. Com foco em aprender cada vez mais
            com as atualizações literárias, sem perder qualidade na efetividade
            prática, na sua empresa buscarei oportunidades semelhantes para
            otimizar processos.
          </p>
        </div>

        <div class="cotainer__skills">
          <h1 class="title">Skills Summary:</h1>
          <ul id="array-rendering" class="demo">
            <div>
              <h1>Fortes</h1>
              <li v-for="(item, idx) in items" :key="idx">
                <div class="niveis">
                  <li v-for="(myicon, idx) in myicons" :key="idx">
                    <font-awesome-icon class="icones" :icon="myicon.myicon" />
                  </li>
                  <div class="linguagens">
                    {{ item.message }}
                  </div>
                </div>
              </li>
            </div>

            <div>
              <h1>Conhecedor</h1>
              <li v-for="item in items2" :key="item.id">
                <div class="niveis">
                  <li v-for="myicon in myicons" :key="myicon.id">
                    <font-awesome-icon class="icones" :icon="myicon.myicon" />
                  </li>
                  <div class="conhecedor">
                    {{ item.message }}
                  </div>
                </div>
              </li>
            </div>
          </ul>
        </div>

        <div class="cotainer__awards">
          <h1 class="title">Awards Received:</h1>
          <ul id="array-rendering" class="demo">
            <div>
              <h1>Awards</h1>
              <li v-for="item in awards" :key="item.id">
                <div class="niveis">
                  <li v-for="myicon in myicons" :key="myicon">
                    <font-awesome-icon class="icones" :icon="myicon.myicon" />
                  </li>
                  <div class="linguagens">
                    {{ item.message }}
                  </div>
                </div>
              </li>
            </div>
          </ul>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";
import { faCircle } from "@fortawesome/free-solid-svg-icons";
import { faCircleNotch } from "@fortawesome/free-solid-svg-icons";


export default {
  name: "MyComponent",

  data() {
    return {
      items: [
        { message: "Java" },
        { message: "JavaScript" },
        { message: "React" },
        { message: "Vue.JS" },
      ],
      items2: [
        { message: "Python" },
        { message: "PHP" },
        { message: "POO" },
        { message: "Estrutura de Dados" },
      ],
      awards: [
        { message: "..." },
        { message: "..." },
        { message: "..." },
        { message: "..." },
        { message: "..." },
      ],
      myicons: [
        { myicon: faCircle },
        { myicon: faCircle },
        { myicon: faCircleNotch },
        { myicon: faCircleNotch },
        { myicon: faCircleNotch },
      ],
    };
  },

  components: {
    FontAwesomeIcon,
  },
};
</script>


<style lang="scss" scoped>
.container {
  justify-content: space-evenly;
}
.hero {
  background: rgb(81, 186, 252);
  height: 250px;
}
.hero-body {
  height: 50px;
  font-weight: 1000px;
}

.container {
  margin-top: -140px;
  margin-left: -50px;
  display: flex;
  padding-right: 5px;
}
.container__about {
  max-width: 540px;
}
h1,
h2 {
  color: #fff;
}

p {
  font-size: 17px;
  line-height: 18px;
}

.demo {
  font-family: sans-serif;
  border: 1px solid #eee;
  border-radius: 2px;
  padding: 20px 30px;
  margin-top: 1em;
  margin-bottom: 40px;
  user-select: none;
  overflow-x: auto;
  display: flex;
}

.niveis {
  display: flex;
  padding-right: 20px;
}

.linguagens, .conhecedor {
  margin-left: 10px;
}


.icones {
  font-size: 8px;
}
</style>
