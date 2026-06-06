
<p align="center">
  <a href="https://git.io/typing-svg">
    <img src="https://readme-typing-svg.herokuapp.com/?color=5a457d&size=35&center=true&vCenter=true&width=1000&lines=MultiplasJanelas3D" alt="MultiplasJanelas3D">
  </a>
</p>

[![Estrelas no GitHub](https://img.shields.io/github/stars/db3n3r/MultipleWindow3DScene?style=social)](https://github.com/db3n3r/MultipleWindow3DScene/stargazers)

<div align="center">
  <img width="1920" height="1028" src="https://github.com/user-attachments/assets/ceee6b65-b659-47ab-a58d-e1f2de87015c" alt="Demonstração do Projeto Multi-Janelas com Three.js" width="1200" />
</div>


<br>
Este é um experimento interativo em WebGL utilizando **Three.js** que quebra as barreiras de uma única janela de navegador. O projeto sincroniza de forma nativa o ambiente espacial entre múltiplas janelas, criando orbes cósmicos de energia volumétrica que reagem fisicamente ao movimento do seu monitor e se conectam através de um feixe de luz quando duas janelas se encontram abertas lado a lado.

## ⭐ Apoie o Projeto

Se este experimento te inspirou ou ajudou nos seus estudos de renderização e manipulação de janelas no navegador, por favor, clique na **estrela (Star)** no topo da página do repositório! Isso dá visibilidade ao projeto e incentiva a criação de novas magias 3D.

## ✨ Características Principais

* **Sincronização Multi-Janelas (Multi-Window Sync):** Utiliza as coordenadas globais da tela (`window.screenX/Y`) e o `localStorage` para rastrear posições de diferentes janelas abertas simultaneamente.
* **Física e Inércia Reativas:** Mover ou sacudir a janela do navegador aplica forças cinéticas (modelo de molas) nas orbes, deformando os rastros de plasma em tempo real baseando-se na inércia vetorial.
* **Renderização Volumétrica Complexa:** 
  * Orbes compostas por camadas de energia (Núcleo denso e Casca extrínseca).
  * Geometria dinâmica e rastros históricos limitados que geram efeito de vida "orgânica" ou plasma correndo sobre uma fronteira constrita.
  * Lógica avançada de visibilidade (View Culling / Dot Product): Os filamentos da casca desaparecem de forma perfeitamente cilíndrica e translúcida apenas na linha de visão da câmera em relação ao núcleo, impedindo que o brilho exterior oculte o centro independente da rotação.
* **Conexão Interdimensional (Feixe):** Quando duas janelas se detectam (numa tolerância temporal rigorosa), um túnel de partículas (Ampulheta) é ativado, conectando as coordenadas espaciais das janelas físicas reais no seu monitor.
* **Post-Processing (Bloom):** Efeitos intensos de neon via `UnrealBloomPass` atrelados à mistura de cor aditiva (`AdditiveBlending`), criando iluminação incandescente real.

## 🚀 Como Executar

Por utilizar [Módulos ES (ESM)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) para carregar o pacote do Three.js via CDN (unpkg), você não precisa usar NPM ou Webpack, mas **é obrigatório rodar em um servidor local** por conta das políticas do [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS).

1. Clone o repositório.
2. Inicie um servidor local na pasta do projeto. 
   - *Via Extensão do VS Code:* Instale o **Live Server** e clique em "Go Live".
   - *Via Python:* `python -m http.server`
   - *Via Node.js:* `npx serve` ou `npx http-server`
3. Abra a aba fornecida pelo servidor (por exemplo, `http://localhost:5500/index.html`).
4. **O Segredo:** Redimensione a aba do navegador nativo para um quadrado (ex: 800x800) e **duplique a janela** (`Ctrl+N` / no Chrome clicar e arrastar a barra). Posicione as duas janelas lado a lado no seu monitor.

## 🧠 Como Funciona a Matemática e Física

- **Coordenadas de Tela:** O código lê nativamente a API da janela para derivar para onde o monitor olharia.
- **Armazenamento Temporal:** Cada janela salva seu UUID de inércia via `localStorage`, avisando todas as outras janelas presentes no mesmo domínio que ela existe e apontando seu vetor. Janelas mortas são destruídas (Garbage Collection de LocalStorage) após 2000ms.
- **Cinemática:** Usa um misto de coordenadas cartesianas limitadas a raios variáveis ($bx, by, bz$) guiadas pelo arrasto de inércia $time$ multiplicado pela janela, o que gera um rastro flutuante nos arrays $Float32$.
- **Transparência Direcional:** Por conta do `AdditiveBlending`, os lados frontais e traseiros da esfera corrompiam a nitidez do núcleo. Implementamos trigonometria profunda (produto escalar de view vectors e Pitágoras 3D) abrindo o miolo virtual independentemente do ângulo de oscilação do objeto instanciado.

## 🛠 Tecnologias Utilizadas

* **HTML5 / CSS3 / Vanilla JS (ES11+)**
* **Three.js (v0.160.0)**
  * `PerspectiveCamera`, `BufferGeometry`, `Line`, `Points`
  * `EffectComposer`, `UnrealBloomPass`, `RenderPass`

## 📝 Licença
Sinta-se à vontade para utilizar para estudo, portfólios ou fork. Modifique com moderação e divirta-se experimentando novas instâncias quânticas pelas abas do seu browser!
