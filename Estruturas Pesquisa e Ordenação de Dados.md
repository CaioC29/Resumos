# Estruturas, pesquisa e ordenação de dados

<br>

## Definição de *Ponteiros

Variáveis que armazenam endereços de memória de outras variáveis

* **Ponteiros** tornam possível:
	* Inserir/remover elementos com flexibilidade.
	* Alocar memória sob demanda.
	* Encadear estruturas complexas mesmo com espaços de memória fragmentados.

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
int desenfileirar(No **fila) {
    if (*fila == NULL) {
        printf("Fila vazia.\n");
        return -1;
    }

    No *remover = *fila;
    int valor = remover->valor;

    *fila = remover->proximo;
    free(remover);

    return valor;
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

<br>

---

**Inserir elemento no meio da lista dupla:**

```c
void inserir_meio(No **lista, int num, int ant){
	
	No *aux, *novo = malloc(sizeof(No));
	
	if(novo){
		novo->valor = num;
		
		if(*lista == NULL){
			novo->proximo = NULL;
			novo->anterior = NULL;
			*lista = novo;
			
		}else{
			aux = *lista;
			
			while(aux->valor != ant && aux->proximo)
				aux = aux->proximo;
			novo->proximo = aux->proximo;
			
			if(aux->proximo){
				aux->proximo->anterior = novo;
			}
			novo->anterior = aux;
			aux->proximo = novo;
		}
	}else{
		printf("Erro ao alocar memoria");
	}
}
```

<br>

---

**Inserir elemento de forma ordenada na lista dupla:**

```c
void inserir_ordenado(No **lista, int num){
    No *aux, *novo = malloc(sizeof(No));

    if(novo){
        novo->valor = num;

        if(*lista == NULL){
            novo->proximo = NULL;
            novo->anterior = NULL;
            *lista = novo;
        }else if(novo->valor < (*lista)->valor){
            novo->proximo = *lista;
            (*lista)->anterior = novo;
            *lista = novo;
        }else{
            aux = *lista;
            while(aux->proximo && novo->valor > aux->proximo->valor)
                aux = aux->proximo;
            novo->proximo = aux->proximo;
            if(aux->proximo)
                aux->proximo->anterior = novo;
            novo->anterior = aux;
            aux->proximo = novo;
        }
    }else
        printf("Erro ao alocar memoria");
}
```

<br>

---

**Remover elemento da lista dupla:**

```c
No* remover(No **lista, int num){
    No *aux, *no = NULL;

    if(*lista){
        if((*lista)->valor == num){
            no = *lista;
            *lista = no->proximo;
            if(*lista)
                (*lista)->anterior = NULL;
        }else{
            aux = *lista;
            while(aux->proximo && aux->proximo->valor != num)
                aux = aux->proximo;
            if(aux->proximo){
                no = aux->proximo;
                aux->proximo = no->proximo;
                if(aux->proximo)
                    aux->proximo->anterior = aux;
            }
        }
    }
    return no;
}
```

<br>

---

**Buscar elemento na lista dupla:**

```c
No* buscar(No **lista, int num){
    No *aux, *no = NULL;

    aux = *lista;
    while(aux && aux->valor != num)
        aux = aux->proximo;
    if(aux)
        no = aux;
    return no;
}
```

<br>

---

**Retornar último nó da lista dupla:**

```c
No* ultimo(No **lista){
    No *aux = *lista;
    while(aux->proximo)
        aux = aux->proximo;
    return aux;
}
```

<br>

---

**Imprimir lista dupla do início ao fim:**

```c
void imprimir_if(No *no){
    printf("\nLista: ");
    while(no){
        printf("%d ", no->valor);
        no = no->proximo;
    }
    printf("\n\n");
}
```

<br>

---

**Imprimir lista dupla do fim ao início:**

```c
void imprimir_do_fim(No **lista) {
    No *aux = *lista;

    // vai até o último nó
    while (aux && aux->proximo) {
        aux = aux->proximo;
    }

    // percorre do fim até o início usando o campo 'anterior'
    printf("\nLista (do fim ao início): ");
    while (aux) {
        printf("%d ", aux->valor);
        aux = aux->anterior;
    }
    printf("\n\n");
}
```

<br><br><br>

## Lista Circular

É uma variação da lista encadeada em que o último nó não aponta para `NULL`, mas sim para o primeiro nó da lista, formando um ciclo fechado. Isso permite que a navegação pelos elementos possa recomeçar automaticamente do início, sem precisar reiniciar a estrutura.

<br>

**Estrutura do nó da lista circular:**

```c
typedef struct no{
	int valor;					 //dado armazenado
	struct no *proximo;			//ponteiro para o próximo nó
}No;



typedef struct{
	No *inicio;
	No *fim;
	int tam;
}Lista;
```

<br>

---

**Inicializar lista circular:**

```c
void criar_lista(Lista *lista){
    lista->inicio = NULL;
    lista->fim = NULL;
    lista->tam = 0;
}
```

<br>

---

**Inserir elemento no início da lista circular:**

```c
void inserir_inicio(Lista *lista, int num){
    No *novo = malloc(sizeof(No));
    if(novo){
        novo->valor = num;
        novo->proximo = lista->inicio;
        lista->inicio = novo;
        if(lista->fim == NULL)
            lista->fim = novo;
        lista->fim->proximo = lista->inicio;
        lista->tam++;
    }else
        printf("Erro ao alocar memoria");
}
```

<br>

---

**Inserir elemento no fim da lista circular:**

```c
void inserir_fim(Lista *lista, int num){
    No *aux, *novo = malloc(sizeof(No));

    if(novo){
        novo->valor = num;
        if(lista->inicio == NULL){
            lista->inicio = novo;
            lista->fim = novo;
            lista->fim->proximo = lista->inicio;
        }else{
            lista->fim->proximo = novo;
            lista->fim = novo;
            novo->proximo = lista->inicio;
        }
        lista->tam++;
    }else
        printf("Erro ao alocar memoria");
}
```

<br>

---

**Inserir elemento de forma ordenada na lista circular:**

```c
void inserir_ordenado(Lista *lista, int num){
    No *aux, *novo = malloc(sizeof(No));

    if(novo){
        novo->valor = num;
        if(lista->inicio == NULL){
            inserir_inicio(lista, num);
        }else if(novo->valor < lista->inicio->valor){
            inserir_inicio(lista, num);
        }else{
            aux = lista->inicio;
            while(aux->proximo != lista->inicio && novo->valor > aux->proximo->valor)
                aux = aux->proximo;

            if(aux->proximo == lista->inicio)
                inserir_fim(lista, num);
            else{
                novo->proximo = aux->proximo;
                aux->proximo = novo;
                lista->tam++;
            }
        }
    }else
        printf("Erro ao alocar memoria");
}
```

<br>

---

**Remover elemento da lista circular:**

```c
No *remover(Lista *lista, int num){
    No *aux, *no = NULL;

    if(lista->inicio){
        if(lista->inicio == lista->fim && lista->inicio->valor == num){
            no = lista->inicio;
            lista->inicio = NULL;
            lista->fim = NULL;
            lista->tam--;
        }else if(lista->inicio->valor == num){
            no = lista->inicio;
            lista->inicio = no->proximo;
            lista->fim->proximo = lista->inicio;
            lista->tam--;
        }else{
            aux = lista->inicio;
            while(aux->proximo != lista->inicio && aux->proximo->valor != num)
                aux = aux->proximo;
            if(aux->proximo->valor == num){
                if(lista->fim == aux->proximo){
                    no = aux->proximo;
                    aux->proximo = no->proximo;
                    lista->fim = aux;
                }else{
                    no = aux->proximo;
                    aux->proximo = no->proximo;
                }
                lista->tam--;
            }
        }
    }
    return no;
}
```

<br>

---

**Buscar elemento na lista circular:**

```c
No *buscar(Lista *lista, int num){
    No *aux = lista->inicio;
    if(aux){
        do{
            if(aux->valor == num)
                return aux;
            aux = aux->proximo;
        }while(aux != lista->inicio);
    }
    return NULL;
}
```

<br>

---

**Imprimir lista circular:**

```c
void imprimir(Lista lista){
    No *no = lista.inicio;
    printf("\n\nLista tam %d: ", lista.tam);
    if(no){
        do{
            printf("%d ", no->valor);
            no = no->proximo;
        }while(no != lista.inicio);
        printf("\nInício: %d\n", no->valor);
    }
    printf("\n\n");
}
```
