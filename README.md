#include <stdio.h>
#include <string.h>
#include <ctype.h>

void trimString(char *str) {
    int start = 0;
    while (isspace(str[start])) start++;
    
    int end = strlen(str) - 1;
    while (end >= start && isspace(str[end])) end--;
    
    memmove(str, str + start, end - start + 1);
    str[end - start + 1] = '\0';  // Null-terminate the trimmed string
}

void question1() {
    char answer;
    printf("Question 1: What is the capital of India?\n");
    printf("a) Mumbai\nb) Delhi\nc) Kolkata\nd) Chennai\n");
    printf("Your answer: ");
    scanf(" %c", &answer);  // Read the answer

    if (tolower(answer) == 'b') {
        printf("Correct!\n\n");
    } else {
        printf("Incorrect. The correct answer is b) Delhi.\n\n");
    }
}

void question2() {
    char answer[100];
    printf("Question 2: Fill in the blank: The chemical symbol for water is _.\n");
    printf("Your answer: ");
    getchar();  // Consume newline from the previous input
    fgets(answer, sizeof(answer), stdin);
    answer[strcspn(answer, "\n")] = '\0';  // Remove newline
    trimString(answer);  // Trim leading/trailing spaces

    if (strcasecmp(answer, "H2O") == 0) {
        printf("Correct!\n\n");
        char string1[50]="the chemical symbol of water is ";
        char string2[] ="H2O";
        strcat(string1,string2);
        printf("Answer:%s\n",string1);
    } else {
        printf("Incorrect. The correct answer is H2O.\n\n");
    }
}

void question3() {
    char answer[100];
    printf(" \n\nQuestion 3: This is a hint-based question. Hint: The answer has 7 words.\n");
    printf("Question:which is the largest planet in our solar system\n");
    printf("Your answer: ");
    fgets(answer, sizeof(answer), stdin);
    answer[strcspn(answer, "\n")] = '\0';  // Remove newline
    trimString(answer);  // Trim leading/trailing spaces

    if (strcasecmp(answer, "jupiter") == 0) {
        printf("Correct!\n\n");
    } else {
        printf("Incorrect. The correct answer is jupiter.\n\n");
    }
}

int main() {
    printf("Welcome to the Quiz!\n\n");

    // Call each question function
    question1();
    question2();
    question3();

    printf("Thank you for participating in the quiz!\n");
    return 0;
}
