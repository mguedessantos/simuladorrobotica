# RoboSim 3D

Simulador de robótica educacional que roda no navegador, em um único arquivo (`index.html`). Monte o robô peça por peça, programe em **blocos** (estilo PictoBlox) ou em **Python** e teste em arenas de segue-linha e de resgate no padrão OBR.

## Como usar

Abra o `index.html` no navegador (é preciso internet, pois as bibliotecas vêm de uma CDN) ou publique o repositório no GitHub Pages.

## Novidades

### Editor de Python
- Botão **🐍 Python** na barra de programação: troca os blocos por um editor onde você digita Python de verdade (variáveis, `if/elif/else`, `for`, `while`, funções, `import random`, `math`).
- O código controla o robô simulado. Erros aparecem no formato do Python, com a linha, e os `print(...)` aparecem na caixa abaixo do editor.
- Lista de comandos dentro do editor (**📖 Comandos do robô**): `mover`, `mover_por`, `motores`, `parar_motores`, `esperar`, `sensor_cor`, `luz`, `distancia`, `giroscopio`, `rotacao_motor`, `zerar_rotacao`, `garra`, `servo_garra`, `garra_segurando`, `objeto_na_garra`, `vitimas`, `temporizador`, `resetar_temporizador`.
- Tab recua e Enter mantém a indentação.
- As funções são da biblioteca do simulador (não existem no Python comum); servem para treinar a lógica e a sintaxe.

### Sensores só funcionam se estiverem montados
- Sensor de cor, ultrassônico, giroscópio e garra não devolvem mais valores padrão quando não estão no robô.
- Ao tentar usá-los, o programa para com uma mensagem clara (por exemplo: "O sensor ultrassônico não está montado no robô."), tanto nos blocos quanto no Python.
- O painel de dados mostra "não montado" no lugar do antigo 400 cm.

## Observações
- Os nomes das funções de Python são ilustrativos e podem ser adaptados a outras bibliotecas de robótica no futuro.
- A parte da OBR (salas e regras) não foi alterada por essas novidades.
