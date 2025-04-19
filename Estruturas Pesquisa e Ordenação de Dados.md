# Estruturas, pesquisa e ordenação de dados

<br>

## Definição de *Ponteiros

Variáveis que armazenam endereços de memória de outras variáveis

<br><br>

## Definição de um Nó
É uma unidade básica de uma estrutura como uma **lista**, e é composto por duas partes:

* Um **valor**
* Um **ponteiro** para o próximo nó

<br>

**Exemplo de estrutura de nó em uma lista *simplesmente encadeada*:**
```c
typedef struct no {
    int valor;                   // dado armazenado
    struct no *proximo;         // ponteiro para o próximo nó
}No;
```
<br><br>

## Estruturas do tipo Lista

A forma de construir e conectar estruturas é muito semelhante, o que muda entre elas é a manipulação

<br><br>

## Pilha

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

---

**Função pop *(desempilhar)*:**

```c
No* pop(No **topo){
	
	if(*topo != NULL){
		No *aux = *topo;
		*topo = aux->proximo;
		return aux; 		//retorna o valor que foi desempilhado
		
	}else{
		printf("A pilha esta vazia");
		return NULL;
	}
	
}
```

<br><br><br>

## Fila

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

---

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

<br><br><br>

## Lista Simplesmente Encadeada

Estrutura em que cada elemento *(nó)* contém um valor e uma referência para o próximo nó. Ela forma uma sequência unidirecional, onde o último nó aponta para `NULL`, indicando o fim da lista.

Pode seguir várias regras, como inserir apenas no final, no início, de forma ordenada, etc.

<br>

**Estrutura do nó da lista simples:**

```c
typedef struct no {
    int valor;                   // dado armazenado
    struct no *proximo;         // ponteiro para o próximo nó
}No;
```

<br>

---

**Inserir elemento no início da lista simples:**

```c
void inserir_inicio(No **lista, int num){

	No *novo = malloc(sizeof(No));
	
	if(novo){
		novo->valor = num;
		novo->proximo = *lista;
		*lista = novo;
	}else{
		printf("Erro ao alocar memoria");
	}
}
```

<br>

---

**Inserir elemento no fim da lista simples:**

```c
void inserir_fim(No **lista, int num){
	
	No *aux, *novo = malloc(sizeof(No));
	
	if(novo){
		novo->valor = num;
		novo->proximo = NULL;
		
		if(*lista == NULL){
			*lista = novo;
		}else{
			aux = *lista;
			while(aux->proximo)
				aux = aux->proximo;
			aux->proximo = novo;
		}
	}else{
		printf("Erro ao alocar memoria");
	}
}
```

<br>

---

**Inserir elemento no meio da lista simples:**

```c
void inserir_meio(No **lista, int num, int ant){
	
	No *aux, *novo = malloc(sizeof(No));
	
	if(novo){
		novo->valor = num;
		
		if(*lista == NULL){
			novo->proximo = NULL;
			*lista = novo;
		}else{
			aux = *lista;
			while(aux->valor != ant && aux->proximo)
				aux = aux->proximo;
			novo->proximo = aux->proximo;
			aux->proximo = novo;
		}
	}else{
		printf("Erro ao alocar memoria");
	}
}
```

<br>

---

**Inserir elemento de forma ordenada na lista simples:**

```c
void inserir_ordenado(No **lista, int num){
	
	No *aux, novo = malloc(sizeof(No));
	
	if(novo){
		novo->valor = num;
		
		if(*lista == NULL){
			novo->proximo = NULL;
			*lista = novo;
			
		}else if(novo->valor < (*lista)->valor){
			novo->proximo = *lista;
			*lista = novo;
			
		}else{
			aux = *lista;
			while(aux->proximo && novo->valor > aux-proximo->valor)
				aux = aux->proximo;
			novo->proximo = aux->proximo;
			aux->proximo = novo;
		}
	}else{
		printf("Erro ao alocar memoria");
	}
}
```

<br>

---

**Imprimir lista simples:**

```c
void imprimir(No *no){
	
	printf("\nLista: ");
	
	while(no){
		prinf("%d ", no->valor);
		no = no->proximo;
	}
	printf("\n\n");
}
```

<br>

---

**Remover um elemento da lista simples:**

```c
No* remover(No **lista, int num){
	
	No *aux, *remove = NULL;
	
	if(*lista){
		if((*lista)->valor == num){
			remover = *lista;
			*lista = remover->proximo;
			
		}else{
			aux = *lista;
			while(aux->proximo && aux->proximo->valor != num)
				aux = aux->proximo;
			if(aux->proximo){
				remove = aux->proximo;
				aux->proximo = remove->proximo;
			}
		}
	}
	return remove;			//retorna o elemento que foi removido
}
```

<br>

---

**Buscar um elemento na lista simples:**

```c
No* buscar(No **lista, int num){
	
	No *aux, *no = NULL;
	aux = *lista;
	
	while(aux && aux->valor != num)
		aux = aux->proximo;
		
	if(aux){
		no = aux;
	}
	return no;
}
```

<br><br><br>


## Lista duplamente encadeada

Estrutura em que cada elemento *(nó)* armazena não só o seu valor, mas também dois ponteiros: um que aponta para o próximo nó e outro que aponta para o anterior. Isso permite que a navegação ocorra em ambas as direções, facilitando inserções e remoções em qualquer posição da lista de forma mais eficiente do que em listas simplesmente encadeadas.

<br>

**Estrutura do nó da lista dupla:**

```c
typedef struct no{
	int valor;					 //dado armazenado
	struct no *proximo;			//ponteiro para o próximo nó
	struct no *anterior;	   //ponteiro para o nó anterior
}No;
```

<br>

---

**Inserir elemento no início da lista dupla:**

```c
void inserir_inicio(No **lista, int num){
	
	No *novo = malloc(sizeof(No));
	
	if(novo){
		novo->valor = num;
		novo->proximo = *lista;
		novo->anterior = NULL;
		
		if(*No **lista){
			(*lista)->anterior = novo;
		}
		*lista = novo;
		
	}else{
		printf("Erro ao alocar memoria");
	}
}
```

<br>

---

**Inserir elemento no fim da lista dupla:**

```c
void inserir_fim(No **lista, int num){
	
	No *aux, *novo = malloc(sizeof(No));
	
	if(novo){
		novo->valor = num;
		novo->proximo = NULL;
		
		if(*lista == NULL){
			*lista = novo;
			novo->anterior = NULL;
			
		}else{
			aux = *lista;
			
			while(aux->proximo)
				aux = aux->proximo;
			aux->proximo = novo;
			novo->anterior = aux;
		}
	}else{
		printf("Erro ao alocar memoria");
	}
}
```
