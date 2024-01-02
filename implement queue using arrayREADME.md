#include <stdio.h>
#define MAX_SIZE 5  

int circularQueue[MAX_SIZE];
int front = -1;
int rear = -1;

int isEmpty() {
    return front == -1;
}

int isFull() {
    return (rear + 1) % MAX_SIZE == front;
}
void enqueue(int num) {
    if (isFull()) {
        printf("Queue is full. Cannot enqueue.\n");
        return;
    }

    if (isEmpty()) {
        front = rear = 0;
    } else {
        rear = (rear + 1) % MAX_SIZE;
    }

    circularQueue[rear] = num;

    printf("%d enqueued successfully.\n", num);
}

void dequeue() {
    if (isEmpty()) {
        printf("Queue is empty. Cannot dequeue.\n");
        return;
    }

    int dequeuedValue = circularQueue[front];

    if (front == rear) {
        front = rear = -1;
    } else {
        front = (front + 1) % MAX_SIZE;
    }

    printf("%d dequeued successfully.\n", dequeuedValue);
}
void display() {
    if (isEmpty()) {
        printf("Queue is empty.\n");
        return;
    }

    printf("Circular Queue elements: ");
    int i = front;
    do {
        printf("%d ", circularQueue[i]);
        i = (i + 1) % MAX_SIZE;
    } while (i != (rear + 1) % MAX_SIZE);

    printf("\n");
}
int peek() {
    if (isEmpty()) {
        printf("Queue is empty. Cannot peek.\n");
        return -1;
    }

    return circularQueue[front];
}
int getRear() {
    if (isEmpty()) {
        printf("Queue is empty. Cannot get rear.\n");
    }

    return circularQueue[rear];

}

int main() {
    enqueue(10);
    enqueue(20);
    enqueue(30);
    display();

    printf("Front (Peek): %d\n", peek());
    printf("Rear: %d\n", getRear());

    dequeue();
    display();

    return 0;
}
C:\Users\devah\Pictures\Screenshots\Screenshot 2024-01-02 132540.png
