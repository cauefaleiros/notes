### 🎮 **Projeto: Controlador de Jogos Baseado em Movimento com Detecção por Cor**

#### **Descrição Geral**

O projeto é um **controlador alternativo para jogos digitais**, desenvolvido com **OpenCV e visão computacional**, que permite jogar títulos simples (como _Pokémon_, _JRPGs_ clássicos e outros com até 8 comandos) **usando apenas movimentos das mãos**, sem teclado ou controle físico.

A inovação está na **diferenciação por cor**:

-   **Fita azul** na mão esquerda → controla **movimentação** (WASD ou setas)
-   **Fita vermelha** na mão direita → controla **ações** (botões A, B, X, Y ou equivalentes)

Ambas as mãos usam **os mesmos gestos de movimento** (cima, baixo, esquerda, direita), mas como o sistema rastreia **cores distintas**, ele sabe exatamente qual ação executar com base na **localização e cor do objeto detectado**.

***

#### **Como Funciona?**

1.  **Captura**: A webcam (ou celular via DroidCam) filma o usuário.
2.  **Detecção por cor**: O sistema converte a imagem para o espaço de cor **HSV** (mais estável que RGB) e isola as cores **azul** e **vermelho** usando máscaras.
3.  **Rastreamento**: Para cada cor, o sistema encontra o maior contorno (a fita) e calcula seu centro (posição X, Y).
4.  **Mapeamento**:
    -   A tela é dividida em **duas zonas** (esquerda e direita) ou em **grids de comando**.
    -   A **posição Y** (cima/baixo) + **posição X** (esquerda/direita) dentro de cada zona define o comando.
    -   Exemplo:
        -   Mão **azul** na parte superior esquerda → **"andar para cima e esquerda"**
        -   Mão **vermelha** na parte inferior direita → **"usar o botão Y"**
5.  **Simulação**: O sistema simula teclas do teclado (ex: `W`, `A`, `Space`, `B`) usando a biblioteca `pynput`, que o jogo interpreta normalmente.

***

#### **Por Que Usar Cores?**

-   **Simplicidade**: Não requer detecção de gestos complexos, machine learning ou treinamento.
-   **Confiança**: Cores bem definidas (fitas) são fáceis de isolar mesmo com variações de luz.
-   **Escalabilidade**: Basta trocar a cor para adicionar novos controles.
-   **Acessibilidade**: Ideal para pessoas com dificuldade motora fina — movimentos amplos substituem pressionar botões pequenos.

***

#### **Tecnologias Utilizadas**

-   **Python 3.11** (versão estável)
-   **OpenCV** (95% do projeto): captura, processamento de imagem, detecção por cor, rastreamento
-   **NumPy**: manipulação de arrays e cálculos geométricos
-   **pynput**: simulação de teclas
-   **DroidCam** (opcional): uso de celular como webcam

***

#### **Objetivo e Valor**

-   **Propósito**: Criar uma **interface de jogo inclusiva, acessível e de baixo custo** (fitas custam menos de R$10).
-   **Originalidade**: Combina simplicidade técnica com utilidade real — poucos projetos acadêmicos focam em **aplicação prática com propósito social**.
-   **Diferencial**: Totalmente controlado por **movimento natural**, sem sensores caros ou hardwares especiais.

***