#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node* next;
} Node;

Node* criarLista() { return NULL; }

int estaVazia(Node* head) { return (head == NULL); }

int tamanhoLista(Node* head) {
    int count = 0;
    for (Node* current = head; current != NULL; current = current->next) count++;
    return count;
}

int obterElemento(Node* head, int pos) {
    if (pos < 1 || pos > tamanhoLista(head)) return -1;
    Node* current = head;
    for (int i = 1; i < pos; i++) current = current->next;
    return current->data;
}

void modificarElemento(Node* head, int pos, int novoValor) {
    if (pos < 1 || pos > tamanhoLista(head)) return;
    Node* current = head;
    for (int i = 1; i < pos; i++) current = current->next;
    current->data = novoValor;
}

Node* inserirElemento(Node* head, int pos, int valor) {
    if (pos < 1 || pos > tamanhoLista(head) + 1) return head;
    Node* novoNo = (Node*)malloc(sizeof(Node));
    novoNo->data = valor;
    if (pos == 1) { novoNo->next = head; return novoNo; }
    Node* current = head;
    for (int i = 1; i < pos - 1; i++) current = current->next;
    novoNo->next = current->next;
    current->next = novoNo;
    return head;
}

Node* removerElemento(Node* head, int pos) {
    if (pos < 1 || pos > tamanhoLista(head)) return head;
    Node* temp;
    if (pos == 1) { temp = head; head = head->next; free(temp); return head; }
    Node* current = head;
    for (int i = 1; i < pos - 1; i++) current = current->next;
    temp = current->next;
    current->next = temp->next;
    free(temp);
    return head;
}

void imprimirLista(Node* head) {
    for (Node* current = head; current != NULL; current = current->next)
        printf("%d -> ", current->data);
    printf("NULL\n");
}

int main() {
    Node* lista = criarLista();
    lista = inserirElemento(lista, 1, 10);
    lista = inserirElemento(lista, 2, 20);
    lista = inserirElemento(lista, 3, 30);
    imprimirLista(lista);
    printf("Elemento na posição 2: %d\n", obterElemento(lista, 2));
    modificarElemento(lista, 2, 25);
    imprimirLista(lista);
    lista = removerElemento(lista, 1);
    imprimirLista(lista);
    return 0;
}
