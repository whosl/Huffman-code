# Huffman-code
#include<stdio.h>
#include<string.h>
#include<stdlib.h>
#define meow (struct tree*)malloc(sizeof(struct tree))
struct tree{
	int gen;
	char name[66];
	struct tree *l,*r;
}; 
struct tree *target,*tar,*v,*u;

void o(struct tree *t,char c[]){
	if(t!=NULL){
		if(strcmp(t->name,c)==0)target=t;
		o(t->l,c);
		o(t->r,c);
	}
}

void finda(struct tree *t,char c[],char e[]){
	if(t!=NULL){

	}
}

int main(){
	int N;
	FILE *in;
	in=fopen("in.txt","r");
	fscanf(in,"%d",&N);
	N--;
	struct tree *top,*p,*insert;
	top=meow;
	top->gen=1;
	p=meow;
	p->l=NULL,p->r=NULL;
	insert=meow;
	p->gen=2,insert->gen=2;
	insert->l=NULL,insert->r=NULL;
	fscanf(in,"%s %s %s",top->name,p->name,insert->name);
	top->l=p;
	top->r=insert;
	while(N--){
		char cn[66];
		fscanf(in,"%s",cn);
		o(top,cn);
		fscanf(in,"%s",insert->name);
		insert->l=NULL,insert->r=NULL;
		insert->gen=target->gen+1;
		insert=target->l;
		fscanf(in,"%s",cn);
		if(strcmp(cn,"NULL")==0)target->r=NULL;
		else{
			insert=meow;
			strcpy(insert->name,cn);
			insert->l=NULL,insert->r=NULL;
			insert->gen=target->gen+1;
			insert=target->r;
		}
	}
	fclose(in);
	char a[66],b[66];
	scanf("%s %s",a,b);
	o(top,a);
	int agen=target->gen;
	o(top,b);
	int bgen=target->gen;
	if(agen>bgen){
		printf("%s %s %d",b,a,agen-bgen);
	}
	else if(agen<bgen){
		printf("%s %s %d",a,b,bgen-agen);
	}
	else{
		finda(top,a,b);
		printf("%s %s %d\n",tar->name,a,agen-tar->gen);
		printf("%s %s %d",tar->name,b,bgen-tar->gen);
	}
	return 0;
}
