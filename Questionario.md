# Questionário Sistemas Embarcados I 
Laura Foroni Braulio 11921EBI012

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
É um modo de compilar códigos em uma plataforma para que seja executado em outra, geralmente é usado no desenvolvimento de software para sistemas embarcados ou na criação de programas com multiplataformas, evitando que seja necessário compilar o código em todas as plataformas de destino.

## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
É um código que inicializa o sistema antes que o código principal seja executado, entabelecendo o ambiente de execução necessário, é geralmente utilizado na configuração de hardware básico.

## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:

#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
O makefile é um conjunto de instruções e arquivos-fonte cuja função é de automatizar o processo de compilação do software e facilitar a manutenção de projetos.

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
Ele analisa um arquivo Makefile para definir quais vão ser compilados e como devem ser, executa os comandos para a compilação, atualiza os artefatos de saída (conforme definido por regras e dependências) e por fim, verifica modificações nos arquivos de origem, compilando só o necessário.

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
target: dependência
     comandos
onde em target coloca-se o nome do target, em dependências são os arquivos que o target depende e em comandos são as ações que devem ser executadas. 

#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
As dependências são definidas através de arquivos ou de outros targets que o target depende. As dependências são usadas para garantir que o make recompile apenas targets que foram alterados nos arquivos de origem, economizando tempo e melhorando a compilação.

#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
São instruções que ditam como criar ou atualizar um target. As regra implícitas são pré definidas, não havendo necessidade de especificar os comandos de compilação.
Já a regra explífita são determinadas pelo usuário, permitindo que o usuário defina e tenha controle sofre as confugurações do target.

## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
O conjunto de instruções Thumb é uma extensão das instruções ARM, oferecendo instruções mais compactas, diminuindo o tamanho do códgio, melhorando o desempenho do cache e o consumo de energia. Ele opera em conjunto com ARM por meio de uma chave de seleção de modo, alternando entre modos durante a execução do código, à dependet da necessidade; 


### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Register***.
A diferença entre as arquiteturas LS e RR está na maneira como as operações de carga/armazenamento são realizadas e como as operações entre registradores são tratadas. A arquitetura LS usa instruções separadas para acessar a memória, enquanto a arquitetura RR permite que as operações aritméticas e lógicas sejam realizadas diretamente entre registradores, sem a necessidade de acessar a memória para cada operação. Isso pode resultar em código mais eficiente, especialmente em operações simples que envolvem registros.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.
Os níveis de acesso são divididos entre privilegiados e não privilegiados. Os privilegiados é nível mais alto, onde o código acessa os recursos do processador e do sistema, tendo controle total sobre ele e podendo operar em operações sensíveis, como alterar parâmetros do hardware e acessar periféricos. Já o não privilegiados é um nível mais baixo, onde o código é limitado, não podendo executar certas instruções ou registros especiais do sistema, prezando pela segurança do sistema.
Os modos de operação é a porta para a mudança dos níveis, sendo eles Thread Mode, Handler Mode e Special Mode. O primeiro se refere ao modo padrão, onde a maioria do código é executado, podendo ser em qualquer um dos níveis. Já o segundo, é usado para acesso privilegiado e lidar com efentos críticos do sistema. Por fim, o Special Mode são modos especiais com configurações  própria para operações específicas e possuem restrição de acesso.

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.
Os processadores ARM tratam exceções e interrupções de forma hierárquica e priorizada. Exceções são eventos durante a execução do programa, enquanto interrupções são externas. Existem diferentes tipos de exceções, como falhas de memória, e as prioridades podem ser configuradas para cada tipo. A estratégia de group priority agrupa exceções e interrupções em níveis de prioridade, com a opção de definir subprioridades para uma granularidade adicional. Isso garante que eventos críticos sejam tratados prontamente, mantendo uma ordem clara de prioridade.

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?
Enquanto o CPSR mostra o estado atual do processador durante a execução do programa, o SPSR salva temporariamento o estado co CPSR durante mudanças de modo ou tratamento de exceções.

### (f) Qual a finalidade do **LR** (***Link Register***)?
Armazenar o endereço de retorno quando uma sub-rotina ou função é chamada.

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?
Armazenar informações sobre o estado atual do processador durante a execução do programa, sendo possível controlar e gerenciar o comportamento do processador.

### (h) O que é a tabela de vetores de interrupção?
Uma estrutura de dados que mapeia fontes de interrupção ou exceção para rotinas, permitindo o direcionando do fluxo de execução para as rotinas de tratamento quando uma interrupção ocorre no processador, sendo ideal para o gerenciaento das interrupções nos sistemas.

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?
O NVIC (Nested Vectored Interrupt Controller) é essencial nos microcontroladores ARM para gerenciar interrupções de forma hierárquica e eficiente. Ele prioriza interrupções, suporta aninhamento de interrupções e controla o estado das interrupções. Em aplicações de tempo real, o NVIC garante tratamento rápido e confiável de interrupções críticas, garantindo que o sistema atenda aos requisitos de tempo e resposta.

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção.
Quando uma interrupção ocorre no Cortex-M, o processador armazena um valor especial, chamado EXC_RETURN, no registrador LR, ao invés do endereço de retorno convencional. Esse valor EXC_RETURN contém informações essenciais sobre o contexto da pilha de exceção e o estado anterior do processador. Após o tratamento da interrupção, o processador utiliza a instrução BX LR para retornar ao estado anterior de execução, fazendo uso das informações contidas no valor EXC_RETURN no registrador LR para restaurar eficientemente a pilha e o estado do processador.

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 
A diferença no salvamento de contexto durante uma interrupção entre Cortex-M3 e Cortex-M4F está no suporte a ponto flutuante do Cortex-M4F, que pode aumentar o tempo e o espaço necessário. Ambos usam a pilha principal, mas o Cortex-M4F pode precisar de mais espaço para os registradores de ponto flutuante. O lazy stack é uma técnica configurável para otimizar o uso da pilha durante interrupções, economizando tempo e memória quando necessário.

## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
