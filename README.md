# TADPilha

#include <stdio.h>
#include <stdlib.h>

// Definição do nodo
typedef struct nodo {
    int info;
    struct nodo *prox;
} nodo;

// Definição da pilha
typedef struct {
    nodo *topo;
} Pilha;

// Protótipos das funções
void inic_pilha(Pilha *p);
void push(Pilha *p, int valor);

int main() {
    Pilha p1, p2;
    int valor = 5;

    // Inicializa as pilhas
    inic_pilha(&p1);
    inic_pilha(&p2);

    // Adiciona valor à pilha p1
    push(&p1, valor);

    printf("Valor %d inserido na pilha p1.\n", valor);
    return 0;
}

// Função para inicializar a pilha
void inic_pilha(Pilha *p) {
    p->topo = NULL;
}

// Função para empilhar (push) um valor
void push(Pilha *p, int valor) {
    nodo *aux;

    // Aloca memória para o novo nodo
    aux = (nodo *)malloc(sizeof(nodo));
    if (!aux) {
        printf("Erro de alocação de memória em push.\n");
        exit(1);
    }

    // Atribui valor ao novo nodo
    aux->info = valor;
    aux->prox = p->topo;  // O novo nodo aponta para o antigo topo
    p->topo = aux;        // Atualiza o topo para o novo nodo
}
