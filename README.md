# Documentação do Programa Ordenacao de Strings com Quick Sort

Este documento descreve um programa de gerenciamento de funcionários escrito em linguagem C. O programa permite que os usuários cadastrem funcionário e visualizem a lista de funcionários cadastrados..

## Arquivos Fonte

### main.c

O arquivo `main.c` é o arquivo principal do programa e contém a função `main()`. Ele é responsável por gerenciar o menu principal e as operações do programa.

### funcionario.c

O arquivo `funcionario.c` contém várias funções relacionadas a funcionários, incluindo preenchimento de dados, ordenação de funcionários e manipulação de arquivos.

#### Funções em `funcionario.c`

1. **`capitalizeString(char *str)`**: Transforma a primeira letra de uma string em maiúscula e o restante em minúscula.

2. **`preencher(Funcionario *funcionario)`**: Preenche os dados de um funcionário, incluindo nome, cargo e documento.

3. **`compararLinhas(const void *a, const void *b)`**: Função de comparação usada para ordenar as linhas do arquivo.

4. **`imprimirArquivo()`**: Lê e imprime o conteúdo do arquivo "funcionarios.txt".

5. **`criarArquivo(Funcionario *funcionario, int n)`**: Cria ou atualiza o arquivo "funcionarios.txt" com os dados dos funcionários.

6. **`ordenarLinhasArquivo()`**: Ordena as linhas do arquivo "funcionarios.txt" em ordem alfabética.

### funcionario.h

O arquivo `funcionario.h` contém as definições de estrutura e protótipos de função utilizados em `funcionario.c`.

#### Estruturas e Protótipos de Função em `funcionario.h`

1. **`Funcionario`**: Estrutura que representa os dados de um funcionário.

2. **`capitalizeString(char *str)`**: Protótipo da função para transformar a primeira letra de uma string em maiúscula e o restante em minúscula.

3. **`preencher(Funcionario *funcionario)`**: Protótipo da função para preencher os dados de um funcionário.

4. **`compararLinhas(const void *a, const void *b)`**: Protótipo da função de comparação usada para ordenar as linhas do arquivo.

5. **`imprimirArquivo()`**: Protótipo da função para imprimir o conteúdo do arquivo "funcionarios.txt".

6. **`criarArquivo(Funcionario *funcionario, int n)`**: Protótipo da função para criar ou atualizar o arquivo "funcionarios.txt" com os dados dos funcionários.

7. **`ordenarLinhasArquivo()`**: Protótipo da função para ordenar as linhas do arquivo "funcionarios.txt" em ordem alfabética.

## Uso do Programa

Para utilizar o programa, siga as seguintes etapas:

1. Compile o programa executando o arquivo `main.c` junto com os arquivos `funcionario.c` e `funcionario.h`.

2. Execute o programa compilado.

3. O programa exibirá um menu com as seguintes opções:
   - "Cadastrar funcionario": Permite ao usuário cadastrar um novo funcionário.
   - "Ver funcionarios": Mostra a lista de funcionários cadastrados em ordem alfabética.
   - "Encerrar programa": Encerra o programa.

4. Siga as instruções do programa para realizar as operações desejadas.

5. Os dados dos funcionários serão armazenados em um arquivo chamado "funcionarios.txt".

## Função QuickSort
# Função Quicksort e Cálculo de T(n)

Aqui está o código da função Quicksort em linguagem C, juntamente com o cálculo de \( T(n) \) de cada linha.

```c
void quicksort(int arr[], int left, int right) {
    if (left < right) {
        int pivot = partition(arr, left, right); // T(n)
        quicksort(arr, left, pivot - 1);         // T(n/2)
        quicksort(arr, pivot + 1, right);        // T(n/2)
    }
}

int partition(int arr[], int left, int right) {
    int pivot = arr[right];       // O(1)
    int i = (left - 1);           // O(1)

    for (int j = left; j <= right - 1; j++) {  // T(n)
        if (arr[j] < pivot) {                  // T(n)
            i++;                               // T(n)
            swap(&arr[i], &arr[j]);            // T(n)
        }
    }

    swap(&arr[i + 1], &arr[right]);   // O(1)
    return (i + 1);                   // O(1)
}

void swap(int* a, int* b) {
    int t = *a;    // O(1)
    *a = *b;       // O(1)
    *b = t;        // O(1)
}
}
```

## Cálculo de \( T(n) \)

Agora, vamos calcular a função \( T(n) \) passo a passo:

1. **Escolha do Pivô**: O tempo gasto para escolher o pivô em uma lista de tamanho \( n \) é \( O(1) \), uma operação constante.

2. **Particionamento**: O tempo gasto para particionar a lista em elementos menores e maiores que o pivô é \( O(n) \), já que precisamos percorrer todos os elementos da lista uma vez.

3. **Recursão**: Após o particionamento, o Quicksort é aplicado recursivamente às duas sublistas resultantes, uma contendo elementos menores que o pivô e a outra contendo elementos maiores. Cada uma dessas chamadas recursivas tem \( T(\frac{n}{2}) \) como tamanho da entrada.

Agora, podemos escrever a função de recorrência para \( T(n) \):

\[ T(n) = O(1) + O(n) + 2T(\frac{n}{2}) \]

A primeira parcela é para a escolha do pivô, a segunda é para o particionamento e a terceira é para as duas chamadas recursivas.

Usando o Teorema Mestre, podemos concluir que o tempo de execução do Quicksort é \( O(n \log n) \).

Portanto:

\[ T(n) = O(n \log n) \]

Isso significa que a complexidade de tempo do algoritmo Quicksort é \( O(n \log n) \).

Agora você tem o código do Quicksort e o cálculo da função \( T(n) \) lado a lado em formato Markdown. Isso deve tornar mais claro como o tempo de execução é calculado em relação ao código.

## Considerações Finais

Este programa oferece funcionalidades básicas de gerenciamento de funcionários, incluindo cadastro, visualização e armazenamento em arquivo. Ele pode ser estendido e aprimorado para atender a requisitos adicionais, como edição e exclusão de funcionários, além de melhorias na interface do usuário.

