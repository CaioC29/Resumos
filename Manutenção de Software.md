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
