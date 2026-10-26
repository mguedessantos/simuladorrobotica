# RoboSim 3D — Simulador 3D de Robótica Educacional

Simulador de robôs **seguidores de linha** e de resgate que roda direto no navegador, em um único arquivo (`index.html`). O aluno monta o robô peça por peça (estilo LEGO), programa em **blocos** ou em **Python** e testa em arenas 3D, seguindo um tutorial de 14 fases.

## Como usar

1. Abra o `index.html` no navegador (Chrome, Edge ou Firefox atualizados). Não precisa instalar nada.
2. É necessária internet na primeira abertura, pois as bibliotecas vêm de CDN (jsDelivr): three.js 0.128, Blockly 10.4.3 e Skulpt 1.2.0.
3. Para publicar, basta hospedar o `index.html` (GitHub Pages, Netlify etc.).

## Modos

| Aba | O que faz |
|---|---|
| **Simular** | Roda o programa do robô na arena. Botões ▶️ Executar, ⏹️ Parar e 🔄 Reiniciar, com controle de velocidade. |
| **Montar robô** | Monta o chassi, motores, rodas, sensores e bateria encaixando peças, como no LEGO. |
| **Montar arena** | Cria arenas com peças de pista (linhas, curvas, cruzamentos, rampas, obstáculos, zona de resgate, ponto final). Inclui 3 salas da OBR 2020 (Nível 1). |
| **Modo livre** | Usa o simulador sem o tutorial. |

O botão **Carregar robô** (e Salvar robô) fica na barra de ferramentas em todas as abas. Robôs são salvos em `.robosim` e arenas em `.arena`.

## Tutorial (14 fases)

| Fase | Tema |
|---|---|
| 1 | Crie seu robô |
| 2 | Faça o robô andar |
| 3 | Virar e contornar |
| 4 | Sensor de cor: ler o chão |
| 5 | Ultrassônico: detectar objetos |
| 6 | Seguir a linha |
| 7 | Curvas fechadas |
| 8 | Linha interrompida |
| 9 | Cruzamento sem marcador |
| 10 | Cruzamento com marcador verde |
| 11 | Beco sem saída (dois verdes) |
| 12 | Obstáculo na linha |
| 13 | Subir a rampa |
| 14 | Desafio completo |

As peças e blocos são liberados aos poucos ao longo das fases. Na Fase 1, o ▶️ **Executar** verifica se o robô está completo e estável.

## Programação

- **Blocos** (Blockly): eventos, movimento, controle, sensores, operadores e variáveis.
- **Python** (Skulpt): editor com destaque de sintaxe, lista de exercícios e salvar/abrir `.py`.
  - **Tab** indenta (4 espaços). **Shift+Tab**, **Shift+Backspace** ou **Shift+Delete** removem a indentação da linha ou das linhas selecionadas.
  - **Ctrl+S** baixa o código.
- Botão ▶️ **Executar** também na janela de programação.

## Novidades

### 2026.10.26 — Mais fases de seguidor de linha e execução simplificada
- 4 novas fases de seguidor de linha: curvas fechadas, linha interrompida, cruzamento sem marcador e beco sem saída (dois verdes). O tutorial agora tem 14 fases (projetos salvos antes são convertidos para a nova numeração).
- O botão Verificar robô foi unido ao ▶️ Executar: na Fase 1 ele confere o robô.
- Novo botão ▶️ Executar na janela de programação (blocos e Python).
- Fase 1: o item "Todas as peças ligadas" saiu da lista (já vinha marcado); a verificação de peças soltas agora faz parte do item do chassi.
- Editor Python: Shift+Backspace, Shift+Delete ou Shift+Tab removem a indentação.
- Carregar robô sempre disponível na barra de ferramentas, em todas as abas.
- Interface mais compacta, com tamanhos que acompanham a janela; na faixa azul do tutorial o texto diminui para caber em vez de ser cortado.

### 2026.10.24 — Pontuação nas arenas montadas
- Arenas montadas com a peça Início valem pontos da OBR (início, percurso, vítimas, chegada).
- A rodada termina quando o programa acaba, com o resumo de pontos no centro da tela.
- Tombou: aviso vermelho no centro, com o motivo.
- Limpar arena também limpa as salas da OBR.
- Salvar/abrir arena e projeto guardam as peças montadas.
- Física: freada limitada pela aderência; tombamento por arrancada/freada só se durar; robôs de 4 rodas sem rodízio não tombam mais ao parar.

### 2026.10.23 — Salas da OBR e novos blocos
- 3 salas reais da OBR 2020 (Nível 1) recriadas na aba Arena.
- Bloco "quando" (roda em paralelo ao programa).
- Girar motor por rotações ou graus, com sentido horário/anti-horário.
- Tutorial com missões curtas e ícones.
- Removidos: ruído dos sensores, desafio da rampa e resgates do criador de mapas.
- Correção: bolinhas presas na parede no desafio 10.

## Reportar problemas

Use o botão **Reportar bug** dentro do simulador.
