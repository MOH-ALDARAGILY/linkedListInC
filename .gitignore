#include <stdio.h>
#include <stdlib.h>

// Define node
typedef struct node
{
    int number;
    struct node* next;
} node;

// Declare funtions
int insertToList(int* counter, int aSizeOfArrayOfNumbers, int* aNumbers, node** aList);
node* setNode(int aNum);
void linkNode(int aCounter, int aIsSorted, node** aCurrentN, node*** aList);
void printList(node* aList);
void freeList(node* aNodeHead);

int main(int argc, char* argv[])
{
    // Initialize list to NULL
    node* list = NULL;

    // Initialize array of input numbers
    int sizeOfArrayOfNumbers = 6;
    int* numbers = malloc(sizeOfArrayOfNumbers * sizeof(int));

    numbers[0] = 7;
    numbers[1] = 6;
    numbers[2] = 5;
    numbers[3] = 4;
    numbers[4] = 2;
    numbers[5] = 8;

    // Initialize counter to 0
    int counter = 0;

    // Insert to list
    int checkReturn;
    checkReturn = insertToList(&counter, sizeOfArrayOfNumbers, numbers, &list);

    // Quit if out of memory
    if (checkReturn == 1)
    {
        return 1;
    }

    // Free array of numbers
    free(numbers);

    // Print list
    printf("1st insertion:\n");
    printList(list);
    printf("\n");

    // Initialize array of input numbers
    sizeOfArrayOfNumbers = 4;
    numbers = malloc(sizeOfArrayOfNumbers * sizeof(int));

    numbers[0] = 0;
    numbers[1] = 1;
    numbers[2] = 3;
    numbers[3] = 9;

    // Insert to list
    checkReturn = insertToList(&counter, sizeOfArrayOfNumbers, numbers, &list);

    // Quit if out of memory
    if (checkReturn == 1)
    {
        return 1;
    }

    // Free array of numbers
    free(numbers);

    // Print list
    printf("2nd insertion:\n");
    printList(list);

    // Free list
    freeList(list);
}

// Insert node/s to list
int insertToList(int* counter, int aSizeOfArrayOfNumbers, int* aNumbers, node** aList)
{
    node* n = NULL;

    // Add 1 to counter
    (*counter)++;

    // Initialize isSorted to true
    int isSorted =1;

    // Check if sorted
    if(*counter == 1)
    {
        for (int j = 0; j < aSizeOfArrayOfNumbers - 1; j++)
        {
            if (aNumbers[j] > aNumbers[j+1])
            {
                isSorted = 0;
                break;
            }
        }
    }

    // Insert nodes
    for (int i = 0; i < aSizeOfArrayOfNumbers; i++)
    {
        // Set node
        n = setNode(aNumbers[i]);

        // Check node
        if (n == NULL)
        {
            return 1;
        }

        // Link node to list
        linkNode(*counter, isSorted, &n, &aList);
    }

    // Return to main function
    return 0;
}

// Set value to node
node* setNode(int aNum)
{
    // Declare pointer to node
    node* aN = malloc(sizeof(node));

    // return NULL if out of memory
    if (aN == NULL)
    {
        return NULL;
    }

    // Set value to node
    aN->number = aNum;
    aN->next = NULL;

    // Return pointer
    return aN;
}

// Link node to list
void linkNode(int aCounter, int aIsSorted, node** aCurrentN, node*** aList)
{
    // Check if list is Empty
    if (**aList == NULL)
    {
        **aList = *aCurrentN;
        return;
    }

    // Initialize a pointer to point where list is pointing
    node* tmp = **aList;

    // If first insertion and isSorted

    if (aCounter == 1 && aIsSorted)
    {
        while (tmp->next != NULL)
        {
            // move to next node
            tmp = tmp->next;
        }
        // Link list to node
        tmp->next = *aCurrentN;

        // return to insertion function
        return;
    }

    // If MIN node
    if ((*aCurrentN)->number < tmp->number)
    {
        // Link node to list
        (*aCurrentN)->next = tmp;

        // Link list to node
        **aList = *aCurrentN;

        // return to insertion function
        return;
    }


    // Find order of node in list
    while (tmp->next != NULL && (*aCurrentN)->number > tmp->next->number)
    {
        // move to next node
        tmp = tmp->next;
    }

    // If MAX node
    if (tmp->next == NULL)
    {
        // Link list to node
        tmp->next = *aCurrentN;

        // return to insertion function
        return;
    }

    // Link node to right part of list
    (*aCurrentN)->next = tmp->next;

    // Link left side of list to node
    tmp->next = *aCurrentN;
}

// Print list
void printList(node* aList)
{
    for(node* tmp = aList; /*Inside the loop*/ ; tmp = tmp->next)
    {
        printf("node: %i\n", tmp->number);
        if (tmp->next == NULL)
        {
            return;
        }
    }
}

// Free list
void freeList(node* aNodeHead)
{
    // Initialize pointer to NULL
    node* tmp = NULL;

    // Free list
    while (aNodeHead != NULL)
    {
        // Assign head to tmp
        tmp = aNodeHead;

        // Go to next node in list
        aNodeHead = aNodeHead->next;

        // free tmp pointer
        free(tmp);
    }
}
