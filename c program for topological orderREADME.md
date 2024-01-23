y deva harsha
192311126
#include <stdio.h>
#include <stdlib.h>


struct Node {
    int data;
    struct Node* next;
};


struct Stack {
    struct Node* top;
};


struct Node* createNode(int data) {
    struct Node* newNode = (struct Node*)malloc(sizeof(struct Node));
    newNode->data = data;
    newNode->next = NULL;
    return newNode;
}

struct Stack* createStack() {
    struct Stack* stack = (struct Stack*)malloc(sizeof(struct Stack));
    stack->top = NULL;
    return stack;
}

void push(struct Stack* stack, int data) {
    struct Node* newNode = createNode(data);
    newNode->next = stack->top;
    stack->top = newNode;
}


int pop(struct Stack* stack) {
    if (stack->top == NULL) {
        return -1; 
    }
    struct Node* temp = stack->top;
    int data = temp->data;
    stack->top = temp->next;
    free(temp);
    return data;
}


void topologicalSortUtil(int v, int visited[], struct Stack* stack, int graph[][100], int numVertices) {
    visited[v] = 1;

    for (int i = 0; i < numVertices; i++) {
        if (graph[v][i] && !visited[i]) {
            topologicalSortUtil(i, visited, stack, graph, numVertices);
        }
    }

    push(stack, v);
}

void topologicalSort(int graph[][100], int numVertices) {
    struct Stack* stack = createStack();
    int visited[100];

    for (int i = 0; i < numVertices; i++) {
        visited[i] = 0;
    }

    for (int i = 0; i < numVertices; i++) {
        if (!visited[i]) {
            topologicalSortUtil(i, visited, stack, graph, numVertices);
        }
    }

    printf("Topological Order: ");
    while (stack->top != NULL) {
        int vertex = pop(stack);
        printf("%d ", vertex);
    }
}

int main() {
    int numVertices, numEdges;

    printf("Enter the number of vertices in the graph: ");
    scanf("%d", &numVertices);

    int graph[100][100] = {0};  

    printf("Enter the number of edges in the graph: ");
    scanf("%d", &numEdges);

    printf("Enter the edges (u v):\n");
    for (int i = 0; i < numEdges; i++) {
        int u, v;
        scanf("%d %d", &u, &v);
        graph[u][v] = 1;  
    }

    topologicalSort(graph, numVertices);

    return 0;
}
