# Bank-Queue-Simulation-Using-Queue-Data-Structure-in-C
```
#include <stdio.h>
#include <stdlib.h>
#define MAX 100

int queue[MAX];
int front = -1;
int rear = -1;
void enqueue(int value)
{
    if(rear == MAX - 1)
    {
        printf("Queue Overflow\n");
        return;
    }

    if(front == -1)
        front = 0;

    queue[++rear] = value;

    printf("Customer %d joined the queue\n", value);
}

int dequeue()
{
    if(front == -1 || front > rear)
    {
        printf("Queue Underflow\n");
        return -1;
    }

    return queue[front++];
}

void display()
{
    if(front == -1 || front > rear)
    {
        printf("No customers waiting\n");
        return;
    }

    printf("Waiting Customers: ");

    for(int i = front; i <= rear; i++)
    {
        printf("%d ", queue[i]);
    }

    printf("\n");
}

int main()
{
    int choice;
    int customer = 1;

    while(1)
    {
        printf("\n--- BANK QUEUE SYSTEM ---\n");
        printf("1. New Customer\n");
        printf("2. Serve Customer\n");
        printf("3. Display Queue\n");
        printf("4. Exit\n");

        printf("Enter choice: ");
        scanf("%d",&choice);

        switch(choice)
        {
            case 1:
                enqueue(customer++);
                break;

            case 2:
            {
                int served = dequeue();

                if(served != -1)
                    printf("Customer %d served\n", served);

                break;
            }

            case 3:
                display();
                break;

            case 4:
                exit(0);
                break;
            default:
                printf("Invalid choice\n");
        }
    }
    return 0;
}
```
