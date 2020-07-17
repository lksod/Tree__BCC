#include <stdio.h>
#include <stdlib.h>
#include <locale.h>



typedef struct no {
	struct no *esq, *dir;
	int chave;
} TNo;

// ---------------------------------------------------------------- Inicializa a árvore
void inicializa(TNo **ptr) {
	*ptr = NULL;
}

// ---------------------------------------------------------------- Insere os valores
void insere(TNo **ptr, int chave) {
	if(*ptr == NULL) {
		(*ptr) = (TNo*) malloc(sizeof(TNo));
		(*ptr)->esq = NULL;
		(*ptr)->dir = NULL;
		(*ptr)->chave = chave;
	} else {
		if(chave < (*ptr)->chave)
			insere(&(*ptr)->esq, chave);
		else if (chave > (*ptr)->chave)
			insere(&(*ptr)->dir, chave);
	}
}

// ---------------------------------------------------------------- Retira os valores 
void antecessor(TNo *q, TNo **r){
	if((*r)->dir != NULL)
		antecessor(q, &(*r)->dir);
	else {
		q->chave = (*r)->chave;
		q = (*r);
		(*r) = (*r)->esq;
		free(q);
	}
}

void retira(TNo **ptr, int chave) {
	if((*ptr) == NULL)
		printf("\n A chave #%d não está na árvore!", chave);
	else if(chave < (*ptr)->chave)
		retira(&(*ptr)->esq, chave);
	else if(chave > (*ptr)->chave)
		retira(&(*ptr)->dir, chave);
	else {
		TNo *aux = *ptr;
		if((*ptr)->dir == NULL) {
			(*ptr) = (*ptr)->esq;
			free(aux);
		} else if((*ptr)->esq == NULL) {
			(*ptr) = (*ptr)->dir;
			free(aux);
		} else antecessor((*ptr), &(*ptr)->esq);
	}
}

// ---------------------------------------------------------------- Função pesquisa
void pesquisa(TNo *ptr, int chave) {
	while((ptr != NULL) && (ptr->chave != chave)) {
		if(chave > ptr->chave)
			ptr = ptr->dir;
		else 
			ptr = ptr->esq;
	}
	if(ptr == NULL) 
		printf("\nA chave #%d não está na árvore\n\n", chave);
	else 
		printf("\nA chave #%d está na árvore\n\n", chave);
}

// ---------------------------------------------------------------- Função imprime in_ordem
void in_ordem(TNo *ptr) {
	if(ptr != NULL) {
		in_ordem(ptr->esq);
		printf("\n %d", ptr->chave);
		in_ordem(ptr->dir);
	}
}

// ---------------------------------------------------------------- Função imprime pre_ordem
void pre_ordem(TNo *ptr) {
	if(ptr != NULL) {
		printf("\n %d", ptr->chave);
		pre_ordem(ptr->esq);
		pre_ordem(ptr->dir);
	}
}

// ---------------------------------------------------------------- Função imprime pos_ordem
void pos_ordem(TNo *ptr) {
	if(ptr != NULL) {
		pos_ordem(ptr->esq);
		pos_ordem(ptr->dir);
		printf("\n %d", ptr->chave);
	}
}
//----------------------------------------------------------------- Função conta filhos 
int Conta_Filho(TNo *ptr, int *filho){
	
	if(ptr != NULL){
		
		Conta_Filho(ptr->esq, filho);
			*filho++;
		Conta_Filho(ptr->dir, filho);
			*filho++;
	}
	printf ("filho: %d\n ",filho);
	return *filho;
}

// -------------------------------------------------------------- Função Encontra nó pai 
void No_Pai(TNo *ptr, int chave){

	int aux = 0;

	while((ptr != NULL) && (ptr->chave != chave)) {
		aux = ptr->chave;
		if(chave > ptr->chave){
			ptr = ptr->dir;
		}else{
			ptr = ptr->esq;
		}
	}
	
	printf ("o no pai de %d e %d\n\n", chave, aux);

}

//--------------------------------------------------------------- Funçâo confere nó irmao 
void No_Irmao(TNo *ptr, int chave){
	TNo *aux ;
		
	while((ptr != NULL) && (ptr->chave != chave)){
		if(chave > ptr->chave){
			aux = ptr->esq;
			ptr = ptr->dir;

		}else{
			aux = ptr->dir;
			ptr = ptr->esq;
		}
	}

	if(aux == NULL){
		printf ("Não exite o nó irmao da chave %d\n\n", chave);
	}else{
		printf ("Existe nó irmão da chave %d\n\n", chave);
	}	
	free(aux);
}

// ---------------------------------------------------------------- Função chama imprime
void imprime(TNo *ptr) {
	int aux=-1;
	
	while(aux != 0) {
		printf("0 - Sair\n1 - in ordem\n2 - pre ordem\n3 - pos ordem\n4 - Conta Filho\n\n");
		scanf("%d", &aux); 
		system("cls");
		
		switch(aux) {
			case 0:
				printf("Pesquisa encerrada.\n\n\n");
			break;
			case 1:
				printf("In ordem\n");
				in_ordem(ptr);
			break;
			case 2:
				printf("Pre ordem\n");
				pre_ordem(ptr);
			break;
			case 3:
				printf("Pos ordem\n");
				pos_ordem(ptr);
			break;
			default:
				system("cls");
			break;
			
		}
		if(aux>=0 && aux<4) printf("\n\n");
	}
}

int main() {
	
	setlocale(LC_ALL,"Portuguese");
	int a[10] = {40, 50, 20, 25, 15, 10, 45, 80, 70, 22}, aux;
	
	TNo *ptr; inicializa(&ptr);
	int filho=-1;
	
	for(int i=0; i<10; i++){
		insere(&ptr, a[i]); 
	}
	
	//printf("!! %d !!",Conta_Filho(ptr, &filho));
	printf("Escreva qual a c")
	//scanf("%d", &aux); retira(&ptr, aux);
	//scanf("%d", &aux); pesquisa(ptr, aux);
	scanf("%d",&aux); No_Irmao(ptr,aux);
	//scanf("%d",&aux); No_Pai(ptr,aux);
	
	imprime(ptr);
	
	return 0;
}
