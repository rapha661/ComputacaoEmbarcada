# Relatório – Computação Embarcada

1.	Introdução
O projeto a seguir foi proposto na disciplina de Computação Móvel e visa contemplar todos os conceitos estudados anteriormente em aula. 
O trabalho consiste na implementação de um jogo no Arduino utilizando C++ como linguagem de programação. O jogo possui três fases sendo a primeira um jogo de memória, na qual os leds piscavam 10 vezes em uma ordem aleatória e o jogador deveria pressionar os respectivos botões que acendiam os leds corretos. Já a segunda fase era uma sequência de perguntas onde o jogador possuía duas chances e precisava acertar cinco questões cujos temas eram variados. Por fim, a terceira fase consiste em uma pergunta “tudo ou nada” onde o jogador, se errar, volta para a primeira fase, mas, caso acerte, ele ganha o jogo. Vale lembrar que o jogo possui um display e um buzzer que servem para exibir a pergunta, avisar que o jogador perdeu, desistiu, ganhou ou passou de fase.

2.	Metodologia
Materiais utilizados:
-	1 Arduino UNO
-	1 LED Vermelho
-	1 LED verde/azul
-	3 botões (push bottom) 
-	Resistores conforme necessidade
-	1 Buzzer
-	1 Display LCD 16x2

Métodos:
O código foi desenvolvido dentro da plataforma tinkercad, para que o programa fique dentro da função de cada fase até que o usuário ganhe, desista ou perca. Dessa forma, foi colocado na função loop somente a verificação da variável global ‘fase’. Ou seja, se a fase for 1, 2 ou 3 a respectiva função é chamada e o programa ficará preso na função da fase até a vitória, derrota ou desistência do jogador.

Na fase 1, o programa fica dentro de um while que verifica quantas jogadas foram feitas, se o jogador está acertando e em que fase está. Dentro do laço, apresenta-se a sequência que deve ser replicada e espera até que o jogador pressione um dos botões. Se o botão pressionado for correto continua. Caso tenha errado, para o laço e chama a função derrota a qual exibe no display que o jogador perdeu, emite um som e volta para o início.

Na fase 2, há um laço for para percorrer no máximo 6 vezes, pois o usuário tem que responder à cinco perguntas e pode errar somente uma vez. Dentro desse for um valor aleatório é gerado e, se não for repetido, armazenado no vetor de perguntas usadas. Depois da sequência de displays, um laço while fica por 10 segundos esperando a resposta do usuário. Ao responder, adiciona no vetor de respostas do usuário e verifica se o vetor de respostas do jogador está igual ao de respostas corretas. Se sim, continua perguntando. Caso contrário, perde uma chance ou perde a fase.

A última fase possui quase o mesmo funcionamento, porém não há chance extra. Portanto chama a função vitória ou derrota.

 ![circuitoCompleto](https://github.com/user-attachments/assets/7c29464b-8cfc-4759-b9c4-e6778bfc6dac)

3.	Experimentos
 
Display para o início do jogo quando fase = 0.
![inicioJogo](https://github.com/user-attachments/assets/dbeb7141-a823-44a7-87e2-b57c1604a9f6)

Display para o começo da fase 1 com apresentação dos leds para memorização.
 ![inicioFase1](https://github.com/user-attachments/assets/ed77714e-b680-4d7c-a9ce-52e30a1d2de2)
 
Display de derrota na fase 1 caso o jogador erre a sequência.
 ![derrotaFase1](https://github.com/user-attachments/assets/4d4972bd-2ac3-41bf-b7a2-5137b7b6e75c)
 
Display avisando que passou da fase 1 e mostrando qual a próxima fase.
 ![passouFase1](https://github.com/user-attachments/assets/8e5ea303-0dd2-45d7-9a92-124d97de596a)

Display de início da fase 2.
 ![inicioFase2](https://github.com/user-attachments/assets/d3d050ee-57f3-4c98-a404-395ec17ce88c)

Display enquanto o jogador não responde à pergunta mostrando o tempo.
 ![tempoFase2](https://github.com/user-attachments/assets/ef5458f0-648f-4a0b-824f-f958b8714da5)

Display para quando acertou a questão. Se tivesse errado, apareceria ‘Errou!’ no display. Se esgotasse o tempo, exibiria ‘Tempo esgotado!’ e o número de chances restantes.
![acertouFase2](https://github.com/user-attachments/assets/abbe059d-ea8a-439e-a1e3-69f476e73cd4)

Display ao passar da fase 2.
 ![passouFase2](https://github.com/user-attachments/assets/7702f1bc-bb45-4ad2-87e7-44ff0433ec7c)

Display de início da fase 3
 ![inicioFase3](https://github.com/user-attachments/assets/76f55477-93e1-484f-b7dc-d328fe561df1)

Display final de vitória e com música no buzzer.
![vitoriaFase3](https://github.com/user-attachments/assets/1a5d3cf5-674c-4cdf-8bc5-d6a2416de5c8)

Vídeo da simulação: https://www.youtube.com/watch?v=h-ndvkRsdEs 

4.	Conclusão
Apesar de ter sido divertido o desenvolvimento do projeto destaca-se algumas dificuldades encontradas durante o processo. Uma delas foi decidir qual botão utilizar com interrupção. Para isso, foi observado que o trabalho pedia para resetar o jogo a qualquer momento e, mesmo que o jogador tivesse que lidar com um delay, era melhor adotar interrupção somente no botão de reset. Outra dificuldade foi durante a fase 2 na parte de exibir o tempo restante para responder à pergunta. Como solução, a condição do laço while foi trocada para verificar somente os botões e dentro do laço há a verificação de exibição do tempo. O último contratempo foi para resetar adequadamente o jogo. Inicialmente o reset era dado pela fase colocada como 0, porém através dessa abordagem o display estava se misturando com o display de início de jogo. Para resolver isso foi usado um código que faz o Arduino começar a ler da linha 0 da memória.

A partir desse projeto, foi possível reforçar os conhecimentos adquiridos em aula e, além disso, utilizar de conceitos novos para aprimorar o trabalho. Outro aspecto importante para destacar é a temática do projeto a qual foi bastante interessante e empolgante de ser trabalhada. Agradecemos pelo suporte dado pelos professores da disciplina e pela proposta do projeto como um todo.
