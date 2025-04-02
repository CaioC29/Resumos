# Manutenção de software

**Responsável por lidar com as mudanças relacionadas ao software depois de sua entrega**

## Manutenibilidade
- Facilidade de manutenção em um sistema
- Difícil de quantificar:
	- Alguns aspectos do sistema podem ser medidos *(ex: complexidade, portabilidade)*


## Métricas de Chidamber-Kemerer (CK): específicas para OO
- Profundidade de herança **(DIT)**
- Número de filhos **(NOC)**
- Acoplamento entre objetos **(CBO)**
- Falta de coesão em métodos **(LCOM)**
- Métodos ponderados por classe **(WMC)**
- Resposta para classe **(RFC)**

## Desenvolvimento vs Manutenção

- Adicionar uma nova funcionalidade durante o desenvolvimento é mais fácil que durante a manutenção
- Manutenção de software deve respeitar certos parâmetros e restrições existentes
- Ex: ao projetar uma nova funcionalidade, o mantedor deve investigar o sistema atual para abstrair sua arquitetura e detalhes de baixo nível
	- Realizar como a  mudança será acomodada
	- Prever o impacto da mudança *(efeito cascata)*
	- Determinar as características necessárias para o trabalho

## Razões para manutenção de software

- Adicionar novas funcionalidades
- Corrigir defeitos
- Melhorar design
- Comunicar com outros sistemas
- Migrar de SO, BD, bibliotecas, etc
- Adaptar a diferentes hardwares
- Adaptar a leis, regras de negócio, etc
- Refatorar código


## Categorias de Manutenção

- Manutenção **C**orretiva
- Manutenção **P**reventiva
- Manutenção **A**daptativa
- Manutenção perfectiva ou **E**volutiva

<img src="https://github.com/user-attachments/assets/fd20901b-ff11-470b-996a-17695855ea76" height="auto" width="600">


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

## Proporção de manutenção

<img src="https://github.com/user-attachments/assets/864b807c-c975-4203-9083-73ce89ee2c00" height="auto" width="300">

## Relacionamento entre as manutenções
- Manutenções são categorizadas de forma individual, mas na prática estão interligadas
- Ao modificar o código devido a uma nova biblioteca *(adaptativa)*, defeitos podem ser introduzidos. Logo, esses defeitos devem ser corrigidos *(corretiva)*
- A introdução de uma nova funcionalidade *(evolutiva)*, pode requerer que o código seja refatorado antes para facilitar sua implementação *(preventiva)*

![image](https://github.com/user-attachments/assets/da4d2f4d-a054-4917-b9bf-9a6106c9c0ec)

- Manutenção **corretiva** e **evolutiva** são mais visíveis e trazem valor direto para o usuário
- Manutenção **preventiva** e **adaptativa** trazem valor indireto para o usuário


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
