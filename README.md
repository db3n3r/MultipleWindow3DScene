<p align="center">
  <a href="https://github.com/db3n3r/MultipleWindow3DScene">
    <img src="https://readme-typing-svg.herokuapp.com/?color=5a457d&size=35&center=true&vCenter=true&width=1000&lines=MultiplasJanelas3D" alt="MultiplasJanelas3D">
  </a>
</p>

<p align="center">
    <img alt="Three.js" src="https://img.shields.io/badge/threejs-black?style=for-the-badge&logo=three.js&logoColor=white">
  <img alt="JavaScript" src="https://img.shields.io/badge/javascript-%23323330.svg?style=for-the-badge&logo=javascript&logoColor=%23F7DF1E">
  <img alt="HTML5" src="https://img.shields.io/badge/html5-%23E34F26.svg?style=for-the-badge&logo=html5&logoColor=white">
</p>

<div align="center">
  <img width="100%" src="https://github.com/user-attachments/assets/4b1254c8-e47b-42c8-866b-dd6fba4067a7" alt="Demonstração do Projeto Multi-Janelas com Three.js" />
</div>

<br>

Este é um experimento interativo em WebGL utilizando **Three.js** que quebra as barreiras de uma única janela de navegador. O projeto sincroniza de forma nativa o ambiente espacial entre múltiplas janelas, criando orbes cósmicas de energia volumétrica que reagem fisicamente ao movimento do seu monitor e se conectam através de um feixe de luz quando duas instâncias se encontram abertas lado a lado.

## ✨ Características Principais

* **Sincronização Multi-Janelas:** Utiliza as coordenadas globais da tela (`window.screenX` e `window.screenY`) aliadas ao `localStorage` para rastrear posições de diferentes janelas abertas simultaneamente no mesmo domínio.
* **Física e Inércia Reativas:** Mover ou sacudir a janela do navegador aplica forças cinéticas (modelo de molas) nas orbes, deformando os rastros de plasma em tempo real com base na inércia vetorial.
* **Renderização Volumétrica Complexa:**
  * Orbes compostas por camadas de energia (Núcleo denso e Casca extrínseca).
  * Geometria dinâmica com rastros históricos limitados que geram um efeito "orgânico", simulando plasma fluindo sobre uma fronteira restrita.
  * Lógica avançada de visibilidade (*View Culling*): Os filamentos da casca desaparecem de forma perfeitamente cilíndrica e translúcida apenas na linha de visão da câmera em relação ao núcleo, impedindo que o brilho exterior oculte o centro, independentemente do ângulo de rotação.
* **Conexão Interdimensional:** Quando duas janelas se detectam dentro de uma tolerância temporal rigorosa, um túnel de partículas é ativado, calculando as coordenadas espaciais reais das janelas no seu monitor físico e renderizando um feixe de conexão.
* **Pós-Processamento (Bloom):** Efeitos intensos de neon via `UnrealBloomPass` atrelados à mistura de cor aditiva (`AdditiveBlending`), criando uma iluminação incandescente realista.

## 🚀 Como Executar

Por utilizar [Módulos ES (ESM)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) para carregar o pacote do Three.js via CDN, não é necessário o uso de bundlers como NPM ou Webpack. No entanto, **é obrigatório rodar a aplicação num servidor local** devido às políticas de [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS).

1. Clone este repositório:
   ```bash
   git clone [https://github.com/db3n3r/MultipleWindow3DScene.git](https://github.com/db3n3r/MultipleWindow3DScene.git)
   ```
2. Inicie um servidor web local na raiz do projeto. Escolha a sua opção preferida:
   - **VS Code:** Instale a extensão *Live Server* e clique em "Go Live".
   - **Python:** Rode `python -m http.server`
   - **Node.js:** Rode `npx serve` ou `npx http-server`
3. Abra o URL fornecido pelo servidor no seu navegador (ex: `http://localhost:5500/index.html`).
4. **O Segredo:** Redimensione a aba do navegador para um formato mais quadrado (ex: 800x800) e **duplique a janela** (atalho `Ctrl+N` ou arraste a aba para fora). Posicione as duas janelas lado a lado no seu monitor e veja a mágica acontecer.

## 🧠 Arquitetura e Física (Under the Hood)

- **Coordenadas de Tela:** O código lê nativamente a API `window` do navegador para derivar a angulação e o posicionamento absoluto da câmera virtual em relação ao monitor físico.
- **Armazenamento e Sincronização:** Cada janela salva o seu UUID de inércia via `localStorage`, realizando um *broadcast* da sua existência e do seu vetor de posição para as demais janelas. Instâncias fechadas sofrem *Garbage Collection* no armazenamento após 2000ms de inatividade.
- **Cinemática Aplicada:** Utiliza um sistema de coordenadas cartesianas limitadas a raios variáveis ($b_x, b_y, b_z$), guiadas pelo arrasto de inércia atrelado ao tempo ($t$). Isso gera os rastros flutuantes processados através de arrays tipados (`Float32Array`) para otimização de memória.
- **Transparência Direcional:** Devido à natureza do `AdditiveBlending`, faces sobrepostas corrompiam a nitidez do núcleo da orbe. A solução foi implementar trigonometria 3D avançada: calculando o produto escalar ($\vec{v} \cdot \vec{n}$) entre os vetores de visualização e aplicando o teorema de Pitágoras em 3D, garantindo a abertura virtual do núcleo independentemente da oscilação do objeto instanciado.

## 🛠 Tecnologias Utilizadas

* **Linguagens:** HTML5, CSS3, Vanilla JavaScript (ES11+)
* **Biblioteca Gráfica:** [Three.js](https://threejs.org/) (v0.160.0)
* **Componentes Core:** `PerspectiveCamera`, `BufferGeometry`, `Line`, `Points`
* **Post-Processing:** `EffectComposer`, `UnrealBloomPass`, `RenderPass`

## ⭐ Apoie o Projeto
<img alt="GitHub Repo stars" src="https://img.shields.io/github/stars/db3n3r/MultipleWindow3DScene?style=social">
Se este experimento o inspirou, ajudou nos seus estudos de renderização WebGL ou de manipulação de APIs de janela do navegador, considere deixar uma **Estrela (Star)** neste repositório! Isso dá visibilidade ao projeto e incentiva a criação de novos experimentos em 3D.

## 📝 Licença

Sinta-se à vontade para utilizar este código para estudos, testes em portfólios ou realizar um *fork*. Modifique com moderação e divirta-se a experimentar novas instâncias quânticas pelas abas do seu browser!
