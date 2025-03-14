#include <stdio.h>
#include <stdlib.h>
#define MAX 5  // Tamanho máximo da fila

typedef struct {
    int itens[MAX];
    int frente, tras;
} Fila;

// Inicializa a fila
void inicializarFila(Fila *f) {
    f->frente = 0;
    f->tras = 0;
}

// Verifica se a fila está vazia
int filaVazia(Fila *f) {
    return f->frente == f->tras;
}

// Verifica se a fila está cheia
int filaCheia(Fila *f) {
    return ((f->tras + 1) % MAX) == f->frente;
}

// Insere um elemento no fim da fila
int inserir(Fila *f, int valor) {
    if (filaCheia(f)) {
        printf("Erro: Fila cheia!\n");
        return 0;
    }
    f->itens[f->tras] = valor;
    f->tras = (f->tras + 1) % MAX;
    return 1;
}

// Remove um elemento do início da fila
int remover(Fila *f, int *valor) {
    if (filaVazia(f)) {
        printf("Erro: Fila vazia!\n");
        return 0;
    }
    *valor = f->itens[f->frente];
    f->frente = (f->frente + 1) % MAX;
    return 1;
}

// Consulta o início da fila sem remover
int consultar(Fila *f, int *valor) {
    if (filaVazia(f)) {
        printf("Erro: Fila vazia!\n");
        return 0;
    }
    *valor = f->itens[f->frente];
    return 1;
}

// Imprime a fila
void imprimirFila(Fila *f) {
    if (filaVazia(f)) {
        printf("Fila vazia!\n");
        return;
    }
    printf("Fila: ");
    for (int i = f->frente; i != f->tras; i = (i + 1) % MAX) {
        printf("%d ", f->itens[i]);
    }
    printf("\n");
}

int main() {
    Fila f;
    int valor;
    inicializarFila(&f);

    inserir(&f, 10);
    inserir(&f, 20);
    inserir(&f, 30);
    inserir(&f, 40);
    imprimirFila(&f);
    
    remover(&f, &valor);
    printf("Removido: %d\n", valor);
    imprimirFila(&f);
    
    consultar(&f, &valor);
    printf("Início da fila: %d\n", valor);
    
    inserir(&f, 50);
    inserir(&f, 60); // Esse deve mostrar erro se a fila estiver cheia
    imprimirFila(&f);
    
    return 0;
}
