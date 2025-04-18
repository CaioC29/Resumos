# Resumo de Estruturas, pesquisa e ordenação de dados

<br>

## Definição de *Ponteiros

Variáveis que armazenam endereços de memória de outras variáveis

<br><br>

## Definição de um Nó
É uma unidade básica de uma estrutura como uma **lista**, e é composto por duas partes:

* Um **valor**
* Um **ponteiro** para o próximo nó

***Exemplo:***
```c
typedef struct no {
    int valor;                   // dado armazenado
    struct no *proximo;         // ponteiro para o próximo nó
}No;
```
<br><br>

## Estruturas do tipo Lista

A forma de construir e conectar estruturas é muito semelhante, o que muda entre elas é a manipulação

### Pilha:
A inserção e remoção de elementos é feita sempre no **topo**

O último elemento a entrar é o primeiro a sair **(LIFO)**

<br>

**Função push *(empilhar)*:**

```c
No* push(No *topo){
	No *novo = malloc(sizeof(No));
	
	if(!novo){
		printf("Erro ao alocar memoria");
		return NULL;
	}else{
		novo->valor = num;
		novo->proximo = topo;
		return novo;
	}
}
```

<br>

**Função pop *(desempilhar)*:**

```c
No* pop(No **topo){
	
	if(*topo != NULL){
		No *aux = *topo;
		*topo = aux->proximo;
		return aux;				//retorna o valor que foi desempilhado
		
	}else{
		printf("A pilha esta vazia");
		return NULL;
	}
	
}
```

<br>

---

<br>

### Fila

A inserção de elementos é feira sempre no final e a remoção no começo

O primeiro elemento a entrar é o primeiro a sair **(FIFO)**

<br>

**Inserir um elemento na fila:**

```c
void enfileirar(No **fila, int num){
	No *aux, *novo = malloc(sizeoff(No));
	
	if(!novo){
		printf("Erro ao alocar memoria");
	}else{
		novo->valor = num;
		novo->proximo = NULL;
		
		if(*fila == NULL){
			*fila = novo;
		}else{
			aux = *fila;
			while(aux->proximo)
				aux = aux->proximo;
			aux->proximo = novo;
		}
	}
}
```

<br>

**Remover um elemento da fila:**

```c
No* desenfileirar(No **fila){
	No *aux = NULL;
	
	if(*fila){
		aux = *fila;
		*fila = aux->proximo;
	}
}
```
