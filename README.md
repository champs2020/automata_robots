# Controle de Sistema de Robôs Autônomos em Armazém

## Introdução

Recentemente, com o rápido desenvolvimento da tecnologia e o advento da Indústria 4.0, a necessidade por automatização dos processos industriais por melhor gerenciamento de recursos e tempo, tornou-se evidente no século XXI. No desenvolvimento de sistemas de controle, uma das abordagens mais comuns é a de tratar o sistema como um autômato finito, sujeito a eventos discretos, que alteram o estado do sistema. Nesse tipo de abordagem, cada parte de um sistema, seus estados e eventos possíveis são projetados e desenvolvidos individualmente,  então podem ser combinadas para formar um sistema maior e mais complexo. Para coordenr o comportamento desse tipo de sistema, faz-se necessária a utilização de controle supervisório, projetado para atuar como uma camada de controle sobre o sistema, restringindo e autorizando transições entre estados para evitar comportamentos indesejados
Nesse projeto, é projetado um sistema de controle supervisório para um conjunto de robôs autômatos que operam em um armazém. Cada robô é projetado individualmente, e as restrições e autorizações necessárias são aplicadas para que o sistema opere como um todo de forma harmônica.

## Objetivos

- Modelar o sistema de transporte de insumos com autômatos finitos;
- Implementar um supervisor para controlar o sistema de forma segura e eficaz;
- Simular e validar os sitema em diferentes cenários.
- Relaizar um vídeo explicando o funcionamento do sistema;

## Materiais e Metodologia

Para o projeto dos robôs e do supervisor, foi utilizado o software [Supremica](#referencia-1), que fornece interface gráfica e operações para lidar com autôatos de forma intuitiva, oq ue permite descrever e simular um sistema a eventos discretos.

O sistema deve funcionar conforme as seguintes regras:
- O sistema é composto por três robôs
  - R1: Transporta do Buffer de Entrada(BE) para as máquinas M1 e M2;
  - R2: Transporta do Buffer de Entrada para as máquinas M3 e M4;
  - R3: Substitui qualquer um dos robôs em caso de falha;
- Apenas um robô pode acessar o BE por vez para evitar conflitos na retirada de insumos.
- Se um robô estiver retirando um insumo, o outro deve aguardar.
- Como ambos os robôs passam pelo BE, é necessário um controle para evitar colisões na área.
- Os robôs devem aguardar se o outro estiver no buffer.

A priori, são projetados os autômatos referentes aos robôs, definindo-se seus estados e eventos possíveis. A figura 1 ilustra os estados, eventos possíveis e as relações entre eles referentes aos robôs 1 e 2, que possuem o mesmo modo de operação.

![Autômato R1](imagens/R1.png)  ![Autômato R2](imagens/R2.png)

Os estados definidos para os autômatos R1 e R2 são:
- Idle: O robô está inativos;

Os eventos possíveis para cada autômato são:
-
-

Ambos os robôs estão por padrão inativos. Qualquer um pode ser acionado a qualquer momento, e caso haja uma falha, o autômato fica em um estado de falha, caso não, o robô segue até o buffer de entrada para retirar a carga. A partir daí, ele segue para a máquina designada e volta a ficar inativo após isso.

Note que se um dos robôs falhar, não há como garantir que ee será reinicializado e que a carga será transportada. Para solucionar esse problema, o autômao que representa o comportamento do robô 3 é ilustrado na figura 2.

![Autômato R3](imagens/R3.png)

Os estados do autômato R3 são:
-

Os eventos possíveis do autômato R3 são:
-

No momento em que qualquer um dos autômatos R1 e R2 entrarem em falha, R3 é ativado, e então segue para o buffer de entrada, e então trasporta a carga para a máquina designada









## Referências
1. <a id="referencia-1"></a> > SUPREMICA. Supremica: Supervisor synthesis tool. Disponível em: <https://github.com/robimalik/Supremica>. Acesso em: 11 mar. 2025.
