# Fundamentos de Java

Este documento reúne meus estudos sobre os **fundamentos da linguagem Java**, incluindo **tipos de dados**, **entrada de dados com `Scanner`**, **estruturas condicionais** e **arrays**.
Cada tópico contém explicações, exemplos e exercícios práticos para fixar o conteúdo.

---

## Tipos de Dados em Java

O **Java** é uma **linguagem fortemente tipada**, ou seja, **sempre precisamos declarar o tipo de dado** que será armazenado em uma variável **antes de usá-la**.

Isso traz mais **segurança**, permite **detecção de erros em tempo de compilação** e ajuda o compilador a **otimizar o uso de memória**.

---

### Divisão dos Tipos de Dados

Os tipos de dados em Java se dividem em **dois grandes grupos**:

* **Primitivos**
* **Não Primitivos (Referência)**

---

### Tipos Primitivos

Os tipos primitivos são os mais básicos — **não são objetos** e **não possuem métodos associados**.
Eles armazenam diretamente o valor na memória.

| Tipo      | Tamanho | Exemplo                 | Descrição                              |
| --------- | ------- | ----------------------- | -------------------------------------- |
| `byte`    | 8 bits  | `byte b = 100;`         | Números inteiros pequenos (-128 a 127) |
| `short`   | 16 bits | `short s = 1000;`       | Inteiros menores que `int`             |
| `int`     | 32 bits | `int x = 42;`           | Inteiros mais comuns                   |
| `long`    | 64 bits | `long l = 100000L;`     | Inteiros grandes                       |
| `float`   | 32 bits | `float f = 3.14f;`      | Decimais de precisão simples           |
| `double`  | 64 bits | `double d = 3.14159;`   | Decimais de precisão dupla             |
| `char`    | 16 bits | `char c = 'A';`         | Um único caractere (Unicode)           |
| `boolean` | 1 bit   | `boolean ativo = true;` | Verdadeiro ou falso                    |

📌 **Observação:** tipos primitivos não possuem métodos.
Exemplo inválido: `int.length` ou `boolean.toUpperCase()`.

---

### Tipos Não Primitivos

Também chamados de **tipos de referência**, são **objetos ou estruturas complexas**.
Eles **possuem métodos** e armazenam **referências** para o valor real na memória.

**Exemplos:**

* `String` → texto e manipulação de caracteres
* `Arrays` → coleção de valores do mesmo tipo
* **Objetos** → instâncias de classes
* **Coleções** → `ArrayList`, `HashMap`, `HashSet`, etc.

#### Exemplo:

```java
String nome = "Java";
System.out.println(nome.toUpperCase()); // JAVA

int[] numeros = {1, 2, 3};
System.out.println(numeros.length); // 3
```

---

### Resumo

| Categoria     | Armazena               | Possui métodos? | Exemplo                   |
| ------------- | ---------------------- | --------------- | ------------------------- |
| Primitivo     | Valor direto           | ❌ Não           | `int idade = 25;`         |
| Não Primitivo | Referência para objeto | ✅ Sim           | `String nome = "Fulano";` |

---

##  Entrada de Dados (Classe Scanner)

Os programas precisam **interagir com usuários** — seja via teclado, arquivos ou sistemas externos.
Em Java, usamos a classe **`Scanner`** para capturar dados pelo teclado.

---

### O que é o Scanner?

`Scanner` é uma classe do pacote `java.util` que **lê diferentes tipos de dados**.
Ela funciona como uma **“caixa de entrada”** do programa.

```java
import java.util.Scanner;
```

---

### Criando um Scanner

```java
Scanner input = new Scanner(System.in);
```

Depois do uso, sempre feche o recurso:

```java
input.close();
```

---

### Métodos mais usados

| Tipo de dado          | Método          | Exemplo                                |
| --------------------- | --------------- | -------------------------------------- |
| Inteiro               | `nextInt()`     | `int idade = input.nextInt();`         |
| Decimal (float)       | `nextFloat()`   | `float altura = input.nextFloat();`    |
| Decimal (double)      | `nextDouble()`  | `double peso = input.nextDouble();`    |
| Palavra (sem espaços) | `next()`        | `String nome = input.next();`          |
| Linha (com espaços)   | `nextLine()`    | `String frase = input.nextLine();`     |
| Booleano              | `nextBoolean()` | `boolean ativo = input.nextBoolean();` |

---

### Exemplo Prático

```java
import java.util.Scanner;

public class EntradaDeDados {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.print("Digite um número inteiro: ");
        int numero = input.nextInt();

        System.out.println("Você digitou: " + numero);
        input.close();
    }
}
```

---

### Exercício

Crie um programa que pergunte:

* Nome
* Idade
* Cidade

E exiba:

```
Olá, João! Você tem 25 anos e mora em São Paulo.
```

---

## Estruturas Condicionais

Condicionais são **decisões lógicas** dentro do código.

### If / Else

```java
boolean estradaBloqueada = true;

if (estradaBloqueada) {
    System.out.println("A estrada está bloqueada. Vá por outro caminho.");
} else {
    System.out.println("A estrada está livre! Siga em frente.");
}
```

---

### Else If

```java
int hora = 14;

if (hora < 12) {
    System.out.println("Bom dia!");
} else if (hora < 18) {
    System.out.println("Boa tarde!");
} else {
    System.out.println("Boa noite!");
}
```

---

### Operadores Lógicos

| Operador | Significado | Exemplo                           |         |               |   |        |
| -------- | ----------- | --------------------------------- | ------- | ------------- | - | ------ |
| `&&`     | E (AND)     | `if (idade >= 18 && temCarteira)` |         |               |   |        |
| `        |             | `                                 | OU (OR) | `if (chovendo |   | frio)` |
| `!`      | Negação     | `if (!ativo)`                     |         |               |   |        |

---

### Switch Case

Ideal para **casos específicos**, como menus:

```java
import java.util.Scanner;

public class SwitchCases {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.println("Escolha um Pokémon:");
        System.out.println("1. Bulbasaur");
        System.out.println("2. Charmander");
        System.out.println("3. Squirtle");

        int escolha = input.nextInt();

        switch (escolha) {
            case 1 -> System.out.println("Pai de planta??");
            case 2 -> System.out.println("Parabéns, escolha correta!");
            case 3 -> System.out.println("O cara escolheu uma tartaruga mesmo");
            default -> System.out.println("Pra quem não sabe pra onde vai, qualquer caminho serve!");
        }

        input.close();
    }
}
```

---

## Laços de Repetição e Arrays

### O que é um Array?

Um **array** é uma estrutura que **armazena múltiplos valores do mesmo tipo**.
Imagine como um estacionamento com **vagas numeradas**.

```java
String[] vagas = new String[3];
vagas[0] = "Corsa Rebaixado";
vagas[1] = "Corolla de Idoso";
vagas[2] = null;
```

---

### Percorrendo Arrays

#### Com `for`:

```java
for (int i = 0; i < vagas.length; i++) {
    System.out.println(vagas[i]);
}
```

#### Com `for-each`:

```java
for (String carro : vagas) {
    System.out.println(carro);
}
```

---

### Resumo de Arrays

| Conceito     | Explicação                              |
| ------------ | --------------------------------------- |
| Índice       | Começa em 0                             |
| Tamanho fixo | Não pode mudar após criado              |
| Tipo único   | Todos elementos devem ser do mesmo tipo |
| Tipo de dado | Arrays são objetos                      |
| Acesso       | `nomes[1]` acessa o segundo elemento    |

---
