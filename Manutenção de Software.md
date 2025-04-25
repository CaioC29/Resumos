# Manutenção de software

**Responsável por lidar com as mudanças relacionadas ao software depois de sua entrega**

## Manutenibilidade
- Facilidade de manutenção em um sistema
- Difícil de quantificar:
	- Alguns aspectos do sistema podem ser medidos *(ex: complexidade, portabilidade)*

<br><br>

## Desenvolvimento vs Manutenção

- Adicionar uma nova funcionalidade durante o desenvolvimento é mais fácil que durante a manutenção
- Manutenção de software deve respeitar certos parâmetros e restrições existentes
- Ex: ao projetar uma nova funcionalidade, o mantedor deve investigar o sistema atual para abstrair sua arquitetura e detalhes de baixo nível
	- Realizar como a  mudança será acomodada
	- Prever o impacto da mudança *(efeito cascata)*
	- Determinar as características necessárias para o trabalho

<br><br>

## Razões para manutenção de software

- Adicionar novas funcionalidades
- Corrigir defeitos
- Melhorar design
- Comunicar com outros sistemas
- Migrar de SO, BD, bibliotecas, etc
- Adaptar a diferentes hardwares
- Adaptar a leis, regras de negócio, etc
- Refatorar código

<br><br>

## Categorias de Manutenção

- Manutenção **C**orretiva
- Manutenção **P**reventiva
- Manutenção **A**daptativa
- Manutenção perfectiva ou **E**volutiva


<img src="https://github.com/user-attachments/assets/fd20901b-ff11-470b-996a-17695855ea76" height="auto" width="500">

- **Manutenção Corretiva:**
	- Modificações no software para corrigir defeitos 
	- Pode gerar outros problemas como aumento de complexidade e outros efeitos cascatas
	- *(Ex: defeitos em requisitos, projeto, código)*

- **Manutenção Preventiva:**
	- Modificações no software para prevenir potenciais problemas no futuro
	- Lida com o deterioramento de estruturas. previne falhas e melhora a manutenabilidade
	- Torna os programas mais legíveis e fáceis de entender e facilita manutenções futuras
	- *(Ex: reestruturação de código, otimização, refatoração, atualização da documentação)*

- **Manutenção Adaptativa:**
	- Adaptações para manter o software usável devido às alterações no ambiente externo
	- Ocorre pois o ambiente sofre variações e está em constante evolução, mesmo que não haja defeitos
	- *(Ex: alterações no SO, BD, servidor, compilador, bibliotecas, frameworks, hardware)*

- **Manutenção Perfectiva ou Evolutiva:**
	- Modificações para fornecer melhorias aos usuários
	- Expansão de requisitos do sistema
	- Quando um software se torna útil, os usuário solicitam melhorias além do escopo inicial
	- *(Ex: novas funcionalidades)*

<br><br>

## Proporção de manutenção

<img src="https://github.com/user-attachments/assets/864b807c-c975-4203-9083-73ce89ee2c00" height="auto" width="350">

<br><br>

## Relacionamento entre as manutenções
- Manutenções são categorizadas de forma individual, mas na prática estão interligadas
- Ao modificar o código devido a uma nova biblioteca *(adaptativa)*, defeitos podem ser introduzidos. Logo, esses defeitos devem ser corrigidos *(corretiva)*
- A introdução de uma nova funcionalidade *(evolutiva)*, pode requerer que o código seja refatorado antes para facilitar sua implementação *(preventiva)*

<img src="https://github.com/user-attachments/assets/da4d2f4d-a054-4917-b9bf-9a6106c9c0ec" height="auto" width="500">

- Manutenção **corretiva** e **evolutiva** são mais visíveis e trazem valor direto para o usuário
- Manutenção **preventiva** e **adaptativa** trazem valor indireto para o usuário

<br><br>

## Leis de Lehman

- **Mudança Continua:**
	- O software deve ser continuamente adaptado, senão torna-se menos satisfatório

- **Complexidade Crescente:**
	- Se não forem tomadas medidas para reduzir complexidade, ela irá aumentar progressivamente

- **Crescimento Contínuo:**
	- O software deve ter funcionalidades ampliadas para manter a satisfação dos seus usuários. O projeto inicial não inclui tudo e deve ser aumentado

- **Declínio de Qualidade:**
	- software perde qualidade se não é alterado para refletir as mudanças do ambiente externo

- **Auto Regulação:**
	- O software tende a se auto regular, seguindo padrões previsíveis e comportamentos disciplinados

- **Conservação de estabilidade organizacional:**
	- O software tende a se manter em um nível constante em relação à organização

- **Conservação da familiaridade:**
	- Muitas mudanças no software afetam a familiaridade dos usuários com o software

- **Sistema de Feedback:**
	- A cada nova versão, gera feedback e novas informações e ajustes


<br><br>

## Manutenibilidade

- **Tempo de reconhecimento do problema (MTTI):**
	- Tempo médio para identificar a existência de um problema

- **Tempo de demora administrativa (AD):**
	- Tempo gasto para obter a aprovação para iniciar a correção *(processos burocráticos)*

- **Tempo de correção ou modificação (MTTR):**
	- Tempo médio necessário para solucionar o problema

- **Tempo de teste local e global (TT):**
	- Tempo gasto testando a correção em ambientes locais e globais, incluindo testes unitários, de integração e de regreção

- **Tempo de revisão da manutenção (RAMT):**
	- Tempo necessário para revisar o código corrigido e garantir a sua qualidade antes de liberar para produção

<br><br>

## Métricas de Manutenção

- Tempo médio entre falhas **(MTBF)**
- Tempo médio para reparar **(MTTR)**
- First-Time Fix Rate **(FTFR)**
- Disponibilidade do sistema **(SA)**
- Backlog de manutenção
- Manutenção planejada *x* não planejada
- Custo de manutenção por incidente

<br><br>

## Tempo médio entre falhas (MTBF)

- Utilizado para analisar a concepção do equipamento e/ou sistema e a segurança de ativos complexos
- Baseia-se na relação entre as horas de funcionamento e o número de avarias/bugs
- O MTBF mede o tempo médio que um sistema ou equipamento opera antes de falhar. É utilizado para entender a confiabilidade do ativo e melhorar a programação de manutenção preventiva

***Exemplo:***
*Em um projeto de manutenção de software, se um sistema permanece operacional por 300 horas com 5 falhas, o MTBF seria de 60 horas.*

**Fórmula:**
<br>

$$MTBF = \frac{\text{Tempo Total de Operação}}{\text{Número de Falhas}}$$


<br><br>

## Tempo médio para reparar (MTTR)

Mede o tempo médio necessário para diagnosticar e reparar uma falha. Ele considera desde o início da falha até a retomada da operação normal.

***Exemplo:***
*O sistema falha a cada 120 horas de operação, o que significa que a equipe pode programar manutenções preventivas a cada 100 horas de uso, reduzindo a chance de falhas inesperadas.*

<br>

**Fórmula:**
<br><br>

$$MTTR = \frac{\text{Tempo Total de Reparação}}{\text{Número de Reparaçōes}}$$

<br><br><br><br>

**Fórmula: Tempo médio para reparar (MTTR) para o tempo total de resolução de problemas**
<br><br><br>

$$MTTR = \frac{\text{Total de tempo gasto na resolução de problemas}}{\text{Número de problemas resolvidos}}$$

<br><br><br>

## First-Time Fix Rate (FTFR)

Útil para medir a eficácia do time de manutenção em aplicar soluções robustas e eficientes já na primeira tentativa, o que é crucial para ambientes onde a recorrência de problemas pode gerar atrasos e aumento de custos.

**Fórmula:**
<br><br>

$$FTFR = \frac{\text{Número de problemas corrigidos na primeira tentativa}}{\text{Total de problemas corrigidos}} \times 100$$

<br><br><br>

## Backlog de Manutenção

**Fórmula:**
<br><br>

$$Backlog = \frac{\text{Número total de tarefas de manutenção pendentes}}{\text{Capacidade de resolução da equipe por período}} \times 100$$

<br><br>

## Disponibilidade do Sistema (SA)

Mede o percentual de tempo que o sistema está disponível para uso pelos usuários. Em software, ela é particularmente importante para produtos SaaS, e-commerce ou qualquer software que precise estar sempre online.

**Fórmula:**
<br><br>

$$Disponibilidade = \frac{\text{Tempo de operação}}{\text{Tempo total}} \times 100$$


<br><br>

## Fan-in / Fan-out

- **Fan-in:**
	- Número de funções que chamam uma dada função
	- Valor alto significa grande impacto em mudanças *(propagação)*

- **Fan-out:**
	- Número de funções que foram chamadas por uma função
	- Valor alto significa grande complexidade da função

<br><br>

***Exemplo 1:***

**Suponha que temos os seguintes módulos:**

- **Módulo A:** chamado pelos módulos B, C e D.
- **Módulo B:** chama os módulos E e F.
- **Módulo C:** chama os módulos G e H.

**Calcule Fan-in de A e Fan-out de B e C**
- **Fan-in de A:** 3 (B, C, D)
- **Fan-out de B:** 2 (E, F)
- **Fan-out de C:** 2 (G, H)

<br><br>

***Exemplo 2:***

**Dado o seguinte sistema:**
- **Módulo X:** chamado por A, B.
- **Módulo Y:** chamado por X.
- **Módulo Z:** chamado por X, Y.
- **Módulo W:** chama X, Y, Z.

**Calcule o Fan-in e o Fan-out para os módulos X, Y, Z, e W:**

- **Fan-in de X:** 3 (A, B, W)
- **Fan-out de X:** 2 (Y, Z)
- **Fan-in de Y:** 2 (X, W)
- **Fan-out de Y:** 1 (Z)
- **Fan-in de Z:** 3 (X, Y, W)
- **Fan-out de Z:** 0
- **Fan-in de W:** 0
- **Fan-out de W:** 3 (X, Y, Z)

<br>

## Métricas OO (CK)

Métricas de Chidamber-Kemerer (CK) específicas para sistemas orientados a objetos:

- **Profundidade de herança (DIT)**
	- Representa o número de níveis que uma classe herda métodos e atributos
	- Quanto maior a profundidade, mais complexo o projeto

- **Número de filhos (NOC)**
	- Conta o número de subclasses diretas
	- Mede a largura da hierarquia de uma classe
	- Valor alto pode indicar reuso

- **Acoplamento entre objetos (CBO)**
	- Semelhante a Fan-out
	- Conta classes chamadas por uma classe
	- Quanto mais acoplado uma classe, mais difícil de entender e de manter

- **Falta de coesão em métodos (LCOM)**
	- Para cada par de métodos, métodos que não compartilham atributos menos os que compartilham
	- Mais atributos em comum, maior coesão, menor perda de coesão (LCOM)
	- Baixa coesão aumenta a complexidade

- **Métodos ponderados por classes (WMC)**
	- Atribui pesos aos métodos de uma classe
	- Pode-se pesar os métodos por:
		- Linhas de código
		- Complexidade ciclomática
		- Número de parâmetros

- **Resposta para classe (RFC)**
	- Conta os números de métodos que podem ser executados em resposta a uma mensagem recebida por um objeto
	- Conta o número de métodos da classe mais o número de métodos chamados pelos métodos da classe
	- Quanto maior o RFC, mais complexa é a classe

<br><br>

## Manutenção em modelos tradicionais

### Cascata
* Executa atividades de forma sequencial
* Começa na comunicação e termina na implantação
* Difícil de ocorrer em projetos reais atualmente

<br>

**Quando usar:**
- Quando os requisitos do problema são bem definidos e estáveis
- Quando há pouca chance de mudança nos requisitos
- Sistemas críticos

<br>

**Vantagens:**
- Paradigma mais antigo, estável e testado
- Documentação robusta de cada atividade
- Pode ser combinado com outros modelos
- Simples, atividades são claras e bem definidas

<br>

**Desvantagens:**
- Projetos reais raramente seguem um fluxo sequencial
- Difícil para o cliente definir todos os requisitos antes
- Clientes devem esperar *(versão do produto ficará pronta apenas no final do projeto)*
- Difícil para lidar com mudanças inevitáveis de requisitos
- Atrasos em fases refletem nas demais

<br>

![modelo_cascata](https://cdn.discordapp.com/attachments/1274578228832374906/1365370351311261837/image.png?ex=680d0fbb&is=680bbe3b&hm=b0de8eb3cbbcf940888f414bd396229bbf4880ef3cc2487594121de2ff13db77&)

<br><br>

### Incremental

- Combina elementos do modelo cascata *(linear)* e fluxo paralelo
- Cada sequência produz um incremento *(um produto operacional)*
- Exemplo:
	- Processador de texto:
	- 1° entrega: abrir, editar e salvar documentos
	- 2° entrega: desfazer, refazer, copiar, recortar e colar
	- 3° entrega: corretor ortográfico
	- 4° entrega: configuração de layout

**Quando usar:**
- Requisitos de software estão razoavelmente definidos
- Escopo de desenvolvimento não pode ser puramente linear
- Necessidade de fornecer número limitado de funcionalidades para usuários rapidamente

<br>

**Vantagens:**
- Custo reduzido para acomodar mudanças
- Feedback do cliente
- Cliente acompanha evolução do sistema
- Início do sistema pelas partes melhor entendidas
- Riscos críticos são resolvidos antes de grandes investimentos

<br>

**Desvantagens:**
- Cuidado ao definir o incremento para que não se aproxime do modelo cascata
- Difícil gerência de software pois o sistema não é completamente especificado anteriormente
- Produto pode se corromper com novos incrementos e se tornar mal estrutura


![modelo_incremental](https://media.discordapp.net/attachments/1274578228832374906/1365371628577357854/image.png?ex=680d10eb&is=680bbf6b&hm=8c7fe720a02c285908f841c879c24f5d5864c758cc09ed12e5b06fd267717720&=&format=webp&quality=lossless)

<br><br>

### Evolucionário

- São iterativos *(repete atividades)*
- Entregam uma versão mais completa do sistema a cada iteração *(curto prazo)*
- Produtos crescem e mudam com o tempo
- Algumas funcionalidades são bem entendidas, mas detalhes precisam ser definidos

**Modelo espiral:**
- Combina a natureza iterativa da prototipação com aspectos sistemáticos do cascata
- Possibilita o desenvolvimento rápido de versões mais completas
- Prototipação no início e incremental depois


![modelo_espiral](https://cdn.discordapp.com/attachments/1274578228832374906/1365379098142183434/image.png?ex=680d17e0&is=680bc660&hm=c911c41ca56ff10224bbf5d11c1c962a3bd5aedb21714a9ece18e6b85f7c600f&)
