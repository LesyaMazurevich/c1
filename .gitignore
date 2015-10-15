#include <stdio.h>                           
#include<stdlib.h>
#include <iostream>
#include <stack>

using namespace std;

struct tree                                  
{ 
    int data;                                
    struct tree *lchild, *mchild, *rchild;   
};

/*
 * функции для итеративного обхода дерева
 */
void iterativeInorder(tree* root) 
{
	stack<tree*> nodeStack;
	tree *_root, *curr = root;
	_root = root;
	for (;;) 
	{
		if (curr != NULL) 
		{
			nodeStack.push(curr);
			curr = curr->lchild;
			continue;
		}
		if (nodeStack.size() == 0) 
		{
			if(_root != NULL)
			{
				curr = _root->rchild;
				_root = NULL;
				continue;
			}
			else return;
		}   
		curr = nodeStack.top();
		nodeStack.pop();
		cout <<  curr->data << " ";
		if(curr->mchild != NULL)
			curr = curr->mchild;
		else 
			curr = curr->rchild;
	}
}

void iterativePreorder(tree* root) 
{
	stack<tree*> nodeStack;
	tree *_root, *curr = root;
	_root = root;
	for (;;) 
	{
		while (curr != NULL) 
		{
			cout << curr->data << " ";
			nodeStack.push(curr);
			curr = curr->lchild;
		}	
		if (nodeStack.size() > 0) 
		{
			curr = nodeStack.top();
			nodeStack.pop();
			if(curr->mchild != NULL)
				curr = curr->mchild;
			else 
				curr = curr->rchild;
		}
		else
		{
			if(_root != NULL)
			{
				curr = _root->rchild;
				_root = NULL;
				continue;
			}
			else return;
		}
	}
}

void iterativePostorder(tree* root) 
{
	tree *curr = root;
	stack<tree*> s1,s2;
	s1.push(curr);
	tree *tmp=NULL;
	while (s1.size() > 0)
	{
		tmp = s1.top();
		s1.pop();
		s2.push(tmp);
		if (tmp->lchild)
			s1.push(tmp->lchild);
		if (tmp->mchild)
			s1.push(tmp->mchild);
		if (tmp->rchild)
			s1.push(tmp->rchild);
	}
	
	while(s2.size() > 0)
	{
		tmp = s2.top();
		s2.pop();
		cout << tmp->data << " ";
	}
}

/*
 * функция для добавления узлов в дерево
 */
struct tree * my_insert(struct tree *p,int n, int dir)               
{
	struct tree *temp;
	temp = (struct tree *)malloc(sizeof(struct tree));
	temp->data = n;
	temp->lchild = temp->rchild=NULL;
	if(p==NULL)
	{
		return temp;
	}
	else
	{
		if(dir ==0) // влево
		{
			p->lchild = temp;
			return temp;
		}
		else if(dir ==1) // посередине
		{
			p->mchild = temp;
			return temp;
		}
		else // вправо
		{
			p->rchild = temp;
			return temp;
		}
	}
}

int main()                                  
{ 
	int x,y,i;                                    
	struct tree *root;
	struct tree *node_2, *node_3, *node_5, *node_8;
	struct tree *node_9, *node_6,*node_10,*node_4, *node_7   ;
		
	root = NULL;
	root = my_insert(root,1,0);		
	node_2 = my_insert(root,2,0);		
	node_3 = my_insert(root,3,1);		
	node_4 = my_insert(root,4,2);		
	node_5 = my_insert(node_3,5,0);		
	node_8 = my_insert(node_5,8,0);		
	node_9 = my_insert(node_5,9,2);		
	node_6 = my_insert(node_3,6,2);		
	node_10 = my_insert(node_6,10,1);		
	node_7 = my_insert(node_4,7,1);		

	iterativeInorder(root);
	printf("\n");
	iterativePreorder(root);
	printf("\n");
	iterativePostorder(root);
	
	return 0;
}
