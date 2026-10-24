# RoboSim 3D

Simulador de robótica educacional que roda no navegador, em um único arquivo (`index.html`). Monte o robô peça por peça, programe em **blocos** (estilo PictoBlox) ou em **Python** e teste em arenas de segue-linha e de resgate no padrão OBR.

## Como usar

Abra o `index.html` no navegador (é preciso internet, pois as bibliotecas vêm de uma CDN) ou publique o repositório no GitHub Pages.

## Novidades

### Editor de Python
- Botão **🐍 Python** na barra de programação: troca os blocos por um editor onde você digita Python de verdade (variáveis, `if/elif/else`, `for`, `while`, funções, `import random`, `math`).
- O código controla o robô simulado. Os `print(...)` aparecem na caixa abaixo do editor.
- Tab recua e Enter mantém a indentação.
- Numeração de linhas e cores de sintaxe no estilo Thonny: palavras-chave, funções do Python, comandos do robô, funções criadas por você, variáveis, textos, números e comentários, com versão para tema claro e escuro.
- Os comandos são da biblioteca do simulador (não existem no Python comum): servem para treinar a lógica e a sintaxe.

### Lista de exercícios de Python
- Botão **📝 Exercícios** (ao lado de 🐍 Python): abre uma lista com 21 exercícios dentro do simulador, acima do editor, para você ler o enunciado enquanto programa.
- Organizada em 4 blocos (variáveis/print/if, laços e listas, funções, integração) mais 3 desafios extras (controle proporcional, contador de cruzamentos e resgate com garra).
- Cada exercício mostra o enunciado, "Pronto quando", o que o robô precisa ter montado (sensores) e uma dica opcional, sem a resposta pronta.
- Caixa para marcar os exercícios concluídos, com contador de progresso. O progresso fica salvo no navegador (se o navegador bloquear o armazenamento, ele só vale até fechar a página).

### Mensagens de erro mais claras
- Os comandos do robô conferem os argumentos antes de executar e explicam o problema em português (comando com argumentos a menos ou a mais, direção escrita errada, velocidade fora do limite, número de sensor inválido, texto no lugar de número).
- Erros do Python (`NameError`, `IndentationError`, erro de sintaxe, `ZeroDivisionError`, `IndexError`, `TypeError`, `ValueError`...) vêm com uma dica 💡 de como corrigir.
- Em nomes digitados errados, o simulador sugere o comando mais parecido ("Você quis dizer 'mover_por'?").

### Sensores só funcionam se estiverem montados
- Sensor de cor, ultrassônico, giroscópio e garra não devolvem valores padrão quando não estão no robô.
- Ao tentar usá-los, o programa para com uma mensagem clara (por exemplo: "O sensor ultrassônico não está montado no robô."), nos blocos e no Python.
- O painel de dados mostra "não montado" no lugar do antigo 400 cm.

## Comandos de Python do robô

Os tempos são em **segundos simulados**: se você acelerar a simulação (2× ou 4×), o tempo real que o robô leva diminui. Todo comando confere a quantidade de argumentos.

### Movimento

| Comando | Argumentos | O que significam |
|---|---|---|
| `mover(direcao, velocidade)` | `direcao`: `"frente"`, `"tras"`, `"esquerda"` ou `"direita"`<br>`velocidade`: número de -100 a 100 | A direção diz para onde o robô vai ou vira. A velocidade é a porcentagem da potência dos motores: 100 é o máximo, 50 é metade, 0 é parado e valores negativos invertem o sentido. O robô continua se movendo até outro comando ou `parar_motores()`. |
| `mover_por(direcao, velocidade, segundos)` | os mesmos de `mover`, mais `segundos`: número de 0 a 3600 | Faz o mesmo que `mover`, mas só pelo tempo indicado (por exemplo, 2.5 = dois segundos e meio). Depois, para os motores sozinho. |
| `motores(esquerdo, direito)` | cada um de -100 a 100 | Potência de cada motor, em %. Valores iguais fazem o robô andar reto; um maior que o outro faz uma curva para o lado do motor mais lento; sinais opostos fazem o robô girar no próprio eixo. É o comando usado em seguidores de linha. |
| `parar_motores()` | nenhum | Zera a potência dos dois motores. |
| `esperar(segundos)` | `segundos`: número de 0 a 3600 | Pausa o programa pelo tempo indicado. O robô mantém o que estava fazendo (por exemplo, continua andando) durante a pausa. |

### Sensores

| Comando | Argumentos | O que devolve |
|---|---|---|
| `sensor_cor(numero_do_sensor)` | número inteiro de 1 a 4 (SC1 a SC4, como numerados na montagem) | O nome da cor vista pelo sensor: `"preto"`, `"verde"`, `"azul"`, `"vermelho"`, `"prata"`, `"branco"` ou `"nenhuma"`. |
| `luz(numero_do_sensor)` | número inteiro de 1 a 4 | A claridade que o sensor vê, de 0 (escuro) a 100 (claro). Útil para controle proporcional. |
| `distancia()` | nenhum | A distância até o obstáculo à frente do ultrassônico, em centímetros. Se não houver nada no alcance, devolve 400. |
| `giroscopio()` | nenhum | O ângulo do robô em graus, de -180 a 180, em relação à direção em que ele começou (0 é a direção inicial). |
| `rotacao_motor(motor)` | `"esquerdo"` ou `"direito"` | Quanto o motor girou, em graus, desde o início ou desde o último `zerar_rotacao()`. |
| `zerar_rotacao()` | nenhum | Volta a contagem de rotação dos dois motores para 0. |
| `temporizador()` | nenhum | Segundos passados desde o início do programa ou do último `resetar_temporizador()`. |
| `resetar_temporizador()` | nenhum | Reinicia o temporizador em 0. |

Sensor ou peça que não estiver montado no robô gera erro, em vez de um valor padrão.

### Garra e resgate

| Comando | Argumentos | O que significam |
|---|---|---|
| `garra(acao)` | `"abrir"` ou `"fechar"` | Abre ou fecha a garra por completo (aberta = 90°, fechada = 0°). |
| `servo_garra(graus)` | número de 0 a 90 | Posição do servo da garra: 0 é fechada e 90 é totalmente aberta. Valores no meio deixam a garra parcialmente aberta. |
| `garra_segurando()` | nenhum | `True` se a garra está segurando algo, senão `False`. |
| `objeto_na_garra()` | nenhum | `True` se há um objeto entre os dedos da garra, senão `False`. |
| `vitimas()` | nenhum | Quantidade de vítimas já dentro da zona de resgate. |

### Outros

| Comando | O que faz |
|---|---|
| `print("texto", valor)` | Mostra texto e valores na caixa abaixo do editor, ótimo para entender o que o robô está lendo. |

## Erros comuns e o que fazer

| Mensagem | O que significa | Como corrigir |
|---|---|---|
| `NameError: name 'x' is not defined` | O Python não conhece esse nome. | Confira a escrita (maiúsculas e minúsculas contam) e se a variável recebeu valor antes do uso. O simulador sugere o nome parecido. |
| `ParseError` / erro de sintaxe | Há algo mal escrito no código. | Confira o `:` no fim de `if`, `elif`, `else`, `while`, `for` e `def`, parênteses e aspas fechados, e `==` para comparar. |
| `IndentationError` | O recuo das linhas está errado. | Use 4 espaços (Tab) dentro de `if`, `while`, `for` e `def`, e alinhe as linhas do mesmo bloco. |
| `TypeError: mover() precisa de 2 argumento(s)...` | Faltam ou sobram argumentos. | Veja as tabelas acima para saber o que cada comando espera. |
| `TypeError: ... deve ser um número` | Foi enviado texto onde se esperava número (por exemplo, `"2"` em vez de `2`). | Tire as aspas ou converta com `int()` ou `float()`. |
| `ValueError: ... deve estar entre ...` | O valor passou do limite aceito. | Use velocidades de -100 a 100 e `servo_garra` de 0 a 90. |
| `ValueError: ... deve ser "frente" ou ...` | A palavra escrita não é uma das opções. | Copie exatamente uma das opções da tabela, sem acento e sem espaços extras. |
| `RuntimeError: O sensor ... não está montado no robô.` | O programa usou uma peça que o robô não tem. | Monte o sensor na aba Montar robô ou tire o comando do código. |
| `ZeroDivisionError` | Houve divisão por zero. | Confira o divisor antes da conta. |
| `IndexError: list index out of range` | Foi pedida uma posição que não existe na lista. | A primeira posição é 0 e a última é `len(lista) - 1`. |

## Observações
- Os nomes das funções de Python são ilustrativos e podem ser adaptados a outras bibliotecas de robótica no futuro.
- A parte da OBR (salas e regras) não foi alterada por essas novidades.
