#include <stdio.h>
#include <stdlib.h>

typedef struct No {
    int valor;
    struct No *esquerda;
    struct No *direita;
} No;

No* criarNo(int valor) {
    No* novo = (No*) malloc(sizeof(No));
    if (novo == NULL) {
        printf("Erro de alocação de memória!\n");
        exit(1);
    }
    novo->valor = valor;
    novo->esquerda = NULL;
    novo->direita = NULL;
    return novo;
}

No* inserir(No* raiz, int valor) {
    if (raiz == NULL) {
        return criarNo(valor);
    }
    if (valor < raiz->valor) {
        raiz->esquerda = inserir(raiz->esquerda, valor);
    } else if (valor > raiz->valor) {
        raiz->direita = inserir(raiz->direita, valor);
    }
    return raiz;
}

int busca(No* raiz, int valor) {
    if (raiz == NULL) {
        return 0;
    }
    if (raiz->valor == valor) {
        return 1;
    }
    if (valor < raiz->valor) {
        return busca(raiz->esquerda, valor);
    } else {
        return busca(raiz->direita, valor);
    }
}

void exibirEmOrdem(No* raiz) {
    if (raiz != NULL) {
        exibirEmOrdem(raiz->esquerda);
        printf("%d ", raiz->valor);
        exibirEmOrdem(raiz->direita);
    }
}

void imprimirArvore(No* raiz, int espaco) {
    if (raiz == NULL) {
        return;
    }
    espaco += 5;
    imprimirArvore(raiz->direita, espaco);
    printf("\n");
    for (int i = 5; i < espaco; i++) {
        printf(" ");
    }
    printf("%d", raiz->valor);
    imprimirArvore(raiz->esquerda, espaco);
}

void liberarArvore(No* raiz) {
    if (raiz != NULL) {
        liberarArvore(raiz->esquerda);
        liberarArvore(raiz->direita);
        free(raiz);
    }
}

int main() {
    No* raiz = NULL;
    int opcao, valor;

    do {
        printf("\n=== MENU ===\n");
        printf("1 - Inserir elemento\n");
        printf("2 - Buscar elemento\n");
        printf("3 - Exibir em ordem\n");
        printf("4 - Exibir arvore\n");
        printf("5 - Reiniciar arvore\n");
        printf("0 - Sair\n");
        printf("Escolha: ");
        
        if (scanf("%d", &opcao) != 1) {
            break;
        }

        switch (opcao) {
            case 1:
                printf("Digite o valor: ");
                scanf("%d", &valor);
                raiz = inserir(raiz, valor);
                printf("Valor inserido!\n");
                break;
            case 2:
                printf("Digite o valor de busca: ");
                scanf("%d", &valor);
                if (busca(raiz, valor)) {
                    printf("Valor encontrado!\n");
                } else {
                    printf("Valor NAO encontrado!\n");
                }
                break;
            case 3:
                printf("Impressao em ordem: ");
                exibirEmOrdem(raiz);
                printf("\n");
                break;
            case 4:
                printf("Impressao da arvore:\n");
                imprimirArvore(raiz, 0);
                printf("\n");
                break;
            case 5:
                liberarArvore(raiz);
                raiz = NULL;
                printf("Arvore reiniciada!\n");
                break;
            case 0:
                printf("Fim do programa!\n");
                break;
            default:
                printf("Opcao invalida!\n");
                break;
        }
    } while (opcao != 0);

    liberarArvore(raiz);
    return 0;
}
