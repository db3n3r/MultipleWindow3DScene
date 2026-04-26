# 🌌 Multi-Window Cosmic Sync (Three.js)

![Three.js](https://img.shields.io/badge/Three.js-r160-black?logo=three.js)
![JavaScript](https://img.shields.io/badge/JavaScript-ES6-yellow.svg)
![License](https://img.shields.io/badge/license-MIT-blue.svg)

Um experimento visual interativo em 3D onde múltiplas janelas do navegador se conectam, compartilham coordenadas físicas na tela do sistema operacional e interagem através de um fluxo de poeira cósmica reativa.

---

## ✨ Funcionalidades (The Magic)

* **Sincronização Cross-Window:** Utiliza a API do `localStorage` para calcular e compartilhar a posição `screenX` e `screenY` absoluta das janelas no monitor em tempo real, permitindo comunicação entre abas sem um servidor.
* **Física Cinética (Kinetic Jelly Physics):** As orbes possuem massa e inércia virtuais. Ao arrastar a janela fisicamente, a esfera "fica para trás" e se deforma no formato de uma gota ou cometa, sendo sugada de volta para o centro por uma física de mola elástica (`Lerp`).
* **Cinemática de Formação (Timeline):** Ao abrir uma segunda janela, o fluxo de energia viaja da orbe principal até o destino. O núcleo da segunda orbe só desperta e cresce após a poeira atingir as coordenadas de destino (1.5s de delay).
* **Matemática de Partículas Avançada:**
    * **Efeito Ampulheta Oca:** O fluxo de conexão aplica uma força de compressão (`pinch`) extrema no centro e um vetor de repulsão (`hollowRadius`) para criar um túnel de vácuo nítido.
    * **Núcleos Ocos:** Tanto as esferas externas quanto os núcleos internos utilizam cálculos de Fresnel para transparência central absoluta.

## 🚀 Como executar localmente

Como o projeto utiliza ES Modules para importar o Three.js (`type="module"`), é necessário um servidor local.

### Opção 1: VS Code (Live Server)
1. Instale a extensão **Live Server**.
2. Clique com o botão direito no `index.html` e selecione **"Open with Live Server"**.

### Opção 2: Node.js
```bash
npx http-server 
```

## 🧠 Lógica Técnica

Resiliência de Arraste: O sistema utiliza birthTimestamp para manter a linha do tempo sincronizada mesmo que o navegador "congele" o JavaScript temporariamente durante o arraste da janela pelo SO.

Física de Mola: A esfera não está presa ao centro; ela persegue o centro da tela usando interpolação linear, criando um efeito elástico natural.

Otimização: Renderização eficiente de milhares de partículas usando BufferGeometry e PointsMaterial com AdditiveBlending.

## 🛠️ Tecnologias
- Three.js
- JavaScript (Vanilla)
- LocalStorage API

## 📄 Licença
Distribuído sob a licença MIT.
