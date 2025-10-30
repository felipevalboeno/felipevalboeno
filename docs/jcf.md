# <span style="color:green;">💼 **Java Collection Framework?**</span>

> 🟢 O que é o JCF (Java Collection Framework)?

A JCF é um sistema completo de estrutura de dados do java, está dentro do pacote Java.util, e possui conjuntos de interfaces, classes e algorítmos para manipular grupos de objetos (como listas, conjuntos, filas e mapas).

Portanto, a JCF engloba as estruturas abaixo da seguinte forma:

-   Interfaces: Definem o que as coleções podem fazer -> Collection, List, Set, Map, Queue

-   Classes Concretas: Implementam as interfaces com diferentes estruturas. -> ArrayList, HashSet, LinkedList

-   Classes utilitárias: Oferecem métodos prontos para manipular coleções. -> Collections, Arrays

-   Acesso e ordenação: Ajudam a  percorrer e a ordenar dados. -> Iterator, Comparator

## Resumo visual estruturado

```
          Iterable
              |
          Collection
       /      |       \
     List     Set     Queue        <-- Interfaces
       |        |        |
 ArrayList  HashSet  LinkedList    <-- Classes concretas
       |
  Collections / Arrays             <-- Classes utilitárias
       |
   Iterator / Comparator            <-- Acesso e ordenação


```
## 🟢 **List**

É uma lista **ordenada** que aceita **elementos repetidos**. Guarda os elementos na ordem de inserção através de **índices**, começando do índice zero.

### Principais formas de Implementação:

-   **ArrayList:** Mais rápido para leitura, porém mais lento para inserção/remoção no meio, pois precisa empurrar os elementos dentro do array.

-    **LinkedList:** Mais rápido para inserção/remoção no meio, mais lento para leitura. Ele não empurra os elementos, mas sim troca a referência dele.

### Quando usar List?

Quando a ordem importar e pode haver repetição.

 
 ```
 import java.util.ArrayList;

public class ExemploArrayList {
    public static void main(String[] args) {
        // Criação de um ArrayList
        ArrayList<String> alunos = new ArrayList<>();

        // Adicionando elementos
        alunos.add("Ana");
        alunos.add("Carlos");
        alunos.add("Beatriz");

        // Inserindo em uma posição específica
        alunos.add(1, "Diego");

        // Acessando elementos pelo índice
        System.out.println("Aluno na posição 2: " + alunos.get(2));

        // Percorrendo com for-each
        System.out.println("Lista de alunos:");
        for (String nome : alunos) {
            System.out.println(nome);
        }

        // Removendo um elemento
        alunos.remove("Carlos");

        System.out.println("\nApós remoção:");
        System.out.println(alunos);
    }
}

Saída esperada:
Aluno na posição 2: Beatriz
Lista de alunos:
Ana
Diego
Carlos
Beatriz

Após remoção:
[Ana, Diego, Beatriz]

 
 ```
### Quando usar ArrayList:

-   Quando você precisa de acesso rápido por índice.

-   Quando faz mais leituras do que inserções/remoções.


```
import java.util.LinkedList;
import java.util.Queue;

public class ExemploLinkedList {
    public static void main(String[] args) {
        // Usando LinkedList como uma fila (Queue)
        Queue<String> fila = new LinkedList<>();

        // Adicionando pessoas à fila
        fila.add("João");
        fila.add("Maria");
        fila.add("Pedro");

        System.out.println("Fila inicial: " + fila);

        // Atendendo (removendo o primeiro)
        String atendido = fila.poll();
        System.out.println("Atendendo: " + atendido);

        // Ver quem é o próximo
        System.out.println("Próximo da fila: " + fila.peek());

        System.out.println("Fila final: " + fila);
    }
}

Saída esperada:
Fila inicial: [João, Maria, Pedro]
Atendendo: João
Próximo da fila: Maria
Fila final: [Maria, Pedro]


```

### Quando usar LinkedList:

-   Quando você precisa inserir ou remover com frequência (principalmente no início/fim).

-   Quando usa estrutura de fila (Queue) ou pilha (Stack).


## 🟢 **Set**

Essa interface não permite elementos repetidos, guardando então elementos únicos e sem índice. A ordem aqui, depende de como você implementa.

### Principais formas de Implementação:

-   **HashSet:** Mais rápido e não garante ordem.

-    **LinkedHashSet:** Mantém a orde de inserção.

-    **TreeSet:** Mantém os elementos em ordem crescente.

### Quando usar Set?

Use o Set quando não puder haver duplicatas.


```
import java.util.HashSet;

public class ExemploHashSet {
    public static void main(String[] args) {
        HashSet<String> frutas = new HashSet<>();

        frutas.add("Banana");
        frutas.add("Maçã");
        frutas.add("Uva");
        frutas.add("Laranja");
        frutas.add("Maçã"); // duplicado — será ignorado

        System.out.println("HashSet:");
        for (String fruta : frutas) {
            System.out.println(fruta);
        }
    }
}

Saída esperada:

HashSet:

Uva

Maçã

Banana

Laranja

```

### Quando usar HashSet?

Quando prescisar verificar a existência de elementos rapidamente.


```

import java.util.LinkedHashSet;

public class ExemploLinkedHashSet {
    public static void main(String[] args) {
        LinkedHashSet<String> cidades = new LinkedHashSet<>();

        cidades.add("São Paulo");
        cidades.add("Rio de Janeiro");
        cidades.add("Curitiba");
        cidades.add("Fortaleza");
        cidades.add("Curitiba"); // duplicado — ignorado

        System.out.println("LinkedHashSet:");
        for (String cidade : cidades) {
            System.out.println(cidade);
        }
    }
}

Saída esperada:

LinkedHashSet:

São Paulo

Rio de Janeiro

Curitiba

Fortaleza

```
### quando usar LinkedHashSet?

Quando você quer unicidade + previsibilidade de ordem, pois ele manter a ordem que os elementos foram adicionados.


```
import java.util.TreeSet;

public class ExemploTreeSet {
    public static void main(String[] args) {
        TreeSet<String> nomes = new TreeSet<>();

        nomes.add("Carlos");
        nomes.add("Ana");
        nomes.add("Pedro");
        nomes.add("Bruna");
        nomes.add("Ana"); // duplicado — ignorado

        System.out.println("TreeSet (ordem alfabética):");
        for (String nome : nomes) {
            System.out.println(nome);
        }
    }
}

Saída esperada:

TreeSet (ordem alfabética):

Ana

Bruna

Carlos

Pedro

```

### Quando usar o TreeSet?

Ideal para listas classificadas sem duplicação e sempre ordenadas.


## 🟢 **Map**

Essa interface trabalha numa estrutura de pares, sendo eles a **chave -> valor** (1-Felipe).
Cada chave é única, mas os valores podem se repetir e o acesso aos elementos é feito por meio da chave.

### Principais formas de Implementação:

-   **HashMap:** Mais rápido e sem ordem.

-    **LinkedHashMap:** Mantém a ordem de inserção.

-    **TreeMap:** Mantém os elementos em ordem crescente, ordenando pela chave.

### Quando usar Map?

Sempre que quiser associar uma chave a um valor — como se fosse um dicionário ou tabela de busca.

```
import java.util.*;

public class ComparacaoMaps {
    public static void main(String[] args) {
        Map<String, Integer> hashMap = new HashMap<>();
        Map<String, Integer> linkedHashMap = new LinkedHashMap<>();
        Map<String, Integer> treeMap = new TreeMap<>();

        List<String> chaves = Arrays.asList("C", "A", "B", "E", "D");

        int valor = 1;
        for (String chave : chaves) {
            hashMap.put(chave, valor);
            linkedHashMap.put(chave, valor);
            treeMap.put(chave, valor);
            valor++;
        }

        System.out.println("HashMap:       " + hashMap);
        System.out.println("LinkedHashMap: " + linkedHashMap);
        System.out.println("TreeMap:       " + treeMap);
    }
}

Saída esperada:

HashMap:       {A=2, B=3, C=1, D=5, E=4}

LinkedHashMap: {C=1, A=2, B=3, E=4, D=5}

TreeMap:       {A=2, B=3, C=1, D=5, E=4}

```
