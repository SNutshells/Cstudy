#include<stdio.h>
#include<stdlib.h>

typedef struct node{
    int  data;
    struct node *next;
}node;

node * qbuild(node *first)
{
	int i,n,a[100];
	node *s;
	printf("输入n:");
	scanf("%d",&n);
	first=(node*)malloc(sizeof(node));
	first->next=NULL;
	for(i=0;i<n;i++)
	{
		s=(node*)malloc(sizeof(node));
		printf("输入a[%d]:",i);
	    scanf("%d",&a[i]);
        s->data=a[i];
		s->next=first->next;
		first->next=s;
	}
	return first;
}


node * hbuild(node *first)
{
	int i,n,a[100];
	struct node *s,*r;
	printf("输入n:");
	scanf("%d",&n);
	first=(node*)malloc(sizeof(node));
	r=first;
	for(i=0;i<n;i++)
	{

		s=(node*)malloc(sizeof(node));
        printf("输入a[%d]:",i);
	    scanf("%d",&a[i]);
		s->data=a[i];
		r->next=s;
        r=s;
	}
	r->next=NULL;
	return first;

}

node * hebing(node *La,node *Lb)
{
	node *pa,*pb,*pc,*Lc;
	pa=La->next;
	pb=Lb->next;
	Lc=pc=La;
	while(pa && pb)
	{
		if(pa->data < pb->data){
			pc->next =pa;
			pc=pa;
			pa=pa->next ;
		}

		else if(pa->data > pb->data){
			pc->next =pb;
			pc=pb;
			pb=pb->next;
		}

	    else{
            pc->next =pa;
			pc=pa;
			pa=pa->next ;
			pb=pb->next ;
		}

	}
	pc->next =pa?pa:pb;
	free(Lb);
    return Lc;
}

node * shanchu(node *first,int i)
{
    node *p,*q;
	p=first->next;
	while(p)
    {
		if((p->next )->data==i)
		{
		   q=p->next  ;
		   p->next =q->next;
		   free(q);
		   break;
		}
		   p=p->next;
	}
	return first;
}

void display(node *first)
{
	struct node *p;
	p=first->next;
	while(p!=NULL)
    {
		printf("%d ",p->data);
		p=p->next;

	}
    printf("\n");
}

int main()
{
	int m;
	struct node *a,*b,*c;
    a=qbuild(a);
    printf("打印链表a：");
    display(a);


    b=hbuild(b);
    printf("打印链表b：");
    display(b);

    c=hebing(a,b);
    printf("打印链表c：");
	display(c);

	printf("输入删除的数m:");
	scanf("%d",&m);
	c=shanchu(c,m);
	printf("打印删除后的链表c:");
	display(c);

    return 0;
}
