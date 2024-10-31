# Resumo para Estudo - Prova de Linguagem C

## 1. Função Recursiva
**Definição**: Uma função é dita recursiva quando chama a si mesma para resolver um problema. Em geral, a recursão é usada para dividir um problema em subproblemas menores, até que chegue a um caso base (condição que encerra a recursão).

**Exemplo**: O cálculo do fatorial de um número, onde `fatorial(n) = n * fatorial(n-1)`. Um caso base seria `fatorial(1) = 1`.

```c
int fatorial(int n) {
    if (n == 1) return 1;  // Caso base
    else return n * fatorial(n - 1);  // Chamada recursiva
}
```

### Exemplo 1: de Fatorial Recursivo
O cálculo do fatorial de um número é um exemplo clássico de recursão. A função `fatorial` multiplica `n` por `fatorial(n-1)` até que `n` chegue a 1.

```c
#include <stdio.h>

int fatorial(int n) {
    if (n == 1) return 1;  // Caso base: fatorial(1) é 1
    else return n * fatorial(n - 1);  // Chamada recursiva
}

int main() {
    int numero = 5;
    printf("Fatorial de %d é %d\n", numero, fatorial(numero)); // Saída: Fatorial de 5 é 120
    return 0;
}
```

### Exemplo 2: de Fibonacci Recursivo
Na sequência de Fibonacci, cada número é a soma dos dois anteriores. Com uma função recursiva, podemos calcular o n-ésimo número de Fibonacci.

```c
#include <stdio.h>

int fibonacci(int n) {
    if (n <= 1) return n;  // Caso base: fibonacci(0) é 0, fibonacci(1) é 1
    return fibonacci(n - 1) + fibonacci(n - 2); // Chamada recursiva
}

int main() {
    int termo = 7;
    printf("Fibonacci de %d é %d\n", termo, fibonacci(termo)); // Saída: Fibonacci de 7 é 13
    return 0;
}
```


## 2. Ponteiros (Definição e Leitura)
**Definição**: Ponteiros são variáveis que armazenam o endereço de memória de outra variável. Eles permitem manipular diretamente os dados armazenados em diferentes posições de memória, o que pode ser mais eficiente.

**Leitura**: int *p define p como um ponteiro para um inteiro. *p (desreferenciação) permite acessar o valor no endereço apontado por p, enquanto & retorna o endereço de uma variável.

```c
int x = 10;
int *p = &x;  // p aponta para o endereço de x
printf("%d", *p);  // Imprime o valor de x (10)
```

### Exemplo 1: de Troca de Valores com Ponteiros
A função troca usa ponteiros para trocar os valores de duas variáveis, modificando-as diretamente.

```c
#include <stdio.h>

void troca(int *a, int *b) {
    int temp = *a;
    *a = *b;
    *b = temp;
}

int main() {
    int x = 10, y = 20;
    troca(&x, &y);
    printf("x = %d, y = %d\n", x, y); // Saída: x = 20, y = 10
    return 0;
}

```

### Exemplo 2: Acessando Elementos de um Vetor com Ponteiros
Um ponteiro pode ser usado para percorrer um vetor e acessar cada elemento pelo endereço.

```c
#include <stdio.h>

int main() {
    int vetor[5] = {1, 2, 3, 4, 5};
    int *p = vetor;

    for (int i = 0; i < 5; i++) {
        printf("%d ", *(p + i)); // Saída: 1 2 3 4 5
    }
    printf("\n");
    return 0;
}
```

## 3. Parâmetros Formais
**Definição**: Parâmetros formais são as variáveis declaradas entre parênteses na definição de uma função. Eles recebem os valores reais passados para a função durante a chamada.

```c
void exemplo(int a, int b) { // 'a' e 'b' são parâmetros formais
    printf("%d, %d", a, b);
}
```

### Exemplo 1: Função com Parâmetros de Soma
Aqui, a e b são parâmetros formais, recebendo os valores passados na chamada da função.

```c
#include <stdio.h>

int soma(int a, int b) { // 'a' e 'b' são parâmetros formais e estão recebendo os valores 3 e 7 respectivamente.
    return a + b;
}

int main() {
    int resultado = soma(3, 7); // valores que estão sendo enviados respectivamente para os parametros formais da função "soma(int a, int b)"
    printf("Soma: %d\n", resultado); // Saída: Soma: 10
    return 0;
}
```

### Exemplo 2: Função para Calcular Média de Três Números
Esta função calcula a média aritmética de três números, usando parâmetros formais.

```c
#include <stdio.h>

float media(int a, int b, int c) { // parametros formais (a recebe 10, b recebe 15 e c recebe 20)
    return (a + b + c) / 3.0;
}

int main() {
    float resultado = media(10, 15, 20);
    printf("Média: %.2f\n", resultado); // Saída: Média: 15.00
    return 0;
}
```

## 4. Função Protótipo
**Definição**: Um protótipo de função é uma declaração que informa ao compilador sobre a função, especificando seu tipo de retorno e parâmetros, sem o corpo da função. Ele é usado para que o compilador reconheça uma função antes de sua definição.

```c
int soma(int a, int b);  // Protótipo da função 'soma'
```

### Exemplo 1: Protótipo para Função de Multiplicação
Os protótipos informam ao compilador que uma função existe antes de sua definição. Isso permite chamar a função antes de ela ser definida no código.
Pode ser declarado dentro ou fora da main(), o professor escolheu declarar o prototipo da função dentro da main().

```c
#include <stdio.h>

int main() {

    int multiplica(int a, int b); // Protótipo da função

    int resultado = multiplica(4, 5); // chamada da função
    printf("Multiplicação: %d\n", resultado); // Saída: Multiplicação: 20
    return 0;
}

int multiplica(int a, int b) { // função
    return a * b;
}
```

## 5. Tamanhos de Tipos de Variáveis
**Definição**: Cada tipo de variável ocupa uma quantidade específica de bytes na memória.

Por exemplo:
- char: 1 byte
- int: geralmente 4 bytes (pode variar)
- float: geralmente 4 bytes
- double: geralmente 8 bytes

A função sizeof pode ser usada para verificar o tamanho de um tipo.
```c
printf("Size of int: %lu\n", sizeof(int));
```

### Exemplo 1: Tamanhos de Tipos de Variáveis
Cada tipo de variável ocupa um espaço específico em memória, e a função sizeof permite verificar o tamanho desses tipos.

```c
#include <stdio.h>

int main() {
    printf("Tamanho de int: %lu bytes\n", sizeof(int));      // Saída: geralmente 4 bytes
    printf("Tamanho de char: %lu byte\n", sizeof(char));     // Saída: 1 byte
    printf("Tamanho de float: %lu bytes\n", sizeof(float));  // Saída: geralmente 4 bytes
    printf("Tamanho de double: %lu bytes\n", sizeof(double));// Saída: geralmente 8 bytes
    return 0;
}

```

## 6. Variável Global
**Definição**: Variáveis globais são declaradas fora de qualquer função e podem ser acessadas por qualquer função do programa. Elas são úteis quando várias funções precisam compartilhar uma mesma informação.

```c
int contador = 0;  // Variável global

void incrementa() {
    contador++;
}
```

### Exemplo 1: Variáveis globais são declaradas fora de funções e podem ser acessadas de qualquer lugar do código.

```c
#include <stdio.h>

int contador = 0;  // Variável global

void incrementa() {
    contador++;
}

int main() {
    incrementa();
    printf("Contador: %d\n", contador); // Saída: Contador: 1
    return 0;
}

```

## 7. Escopo de Variável
**Definição**:  O escopo de uma variável define onde ela pode ser acessada dentro do programa:
- Global: declarada fora das funções e acessível em qualquer parte do código.
- Local: declarada dentro de uma função ou bloco, acessível apenas dentro dessa função/bloco.

### Exemplo 1: O escopo define onde uma variável pode ser acessada. Variáveis locais estão limitadas ao bloco onde foram declaradas, enquanto variáveis globais são acessíveis em todo o programa.

```c
#include <stdio.h>

int global = 10;  // Variável global

void funcao() {
    int local = 5;  // Variável local
    printf("Local: %d, Global: %d\n", local, global); // Saída: Local: 5, Global: 10
}

int main() {
    funcao();
    printf("Global: %d\n", global);  // Saída: Global: 10
    return 0;
}
```

## 8. Função Declarada Antes e Depois da main e Suas Diferenças
**Definição**:  O escopo de uma variável define onde ela pode ser acessada dentro do programa:
- Antes da main(): A função é reconhecida imediatamente e pode ser chamada sem um protótipo.
- Depois da main(): Requer que o protótipo seja declarado antes de main() para informar ao compilador sobre a função.

### Exemplo 1: Declarar uma função antes ou depois da main muda a necessidade de um protótipo. Se uma função é declarada antes da main, ela pode ser usada diretamente; se depois, um protótipo é necessário.

(declarando a função depois da main())
```c
#include <stdio.h>

void saudacao();  // Protótipo da função

int main() {
    saudacao(); // chamada/Saída: Olá, mundo!
    return 0;
}

void saudacao() { // função
    printf("Olá, mundo!\n");
}
```

(declarando antes da main())
```c
#include <stdio.h>

void saudacao() { // função
    printf("Olá, mundo!\n");
}

int main() {
    saudacao(); // chamada/Saída: Olá, mundo!
    return 0;
}

```

## 9. Função Separada em Arquivo
**Definição**: Para organizar o código, as funções podem ser separadas em arquivos .c distintos. Isso melhora a legibilidade e facilita a manutenção. Arquivos de cabeçalho .h são usados para declarar funções e variáveis que podem ser compartilhadas entre arquivos.

```c
Arquivo.h
----------------------------------
// dentro do arquivo arquivo.h 
int funcao(int x);
----------------------------------

main.c
----------------------------------
// dentro do arquivo.c
#include "arquivo.h" // inlui o endereço do arquivo ( se estiver na mesma pasta, chama-se apenas o nome como no exemplo)
int funcao(int x) {
    return x * x;
}
---------------------------------
```


## 10. Impressão de Vetores na Tela
**Definição**: Um vetor é uma coleção de dados do mesmo tipo. Para imprimir um vetor, geralmente usa-se um laço for para acessar cada elemento pelo índice.

```c
#include <stdio.h>

int main() {
    int vetor[5] = {1, 2, 3, 4, 5};
    for (int i = 0; i < 5; i++) {
        printf("%d ", vetor[i]);  // Saída: 1 2 3 4 5
    }
    printf("\n");
    return 0;
}

```

## 11. Structs
**Definição**: Uma struct (estrutura) é um tipo de dado personalizado que permite armazenar vários tipos de dados em um único tipo. É útil para agrupar informações relacionadas.

```c
#include <stdio.h>
#include <string.h>

struct Pessoa {
    char nome[50];
    int idade;
};

int main() {
    struct Pessoa joao;
    joao.idade = 25;
    strcpy(joao.nome, "Joao");

    printf("Nome: %s, Idade: %d\n", joao.nome, joao.idade); // Saída: Nome: Joao, Idade: 25
    return 0;
}

```
