# <span style="color:green;">💼 **Java Stream**</span>

> 🟢 O que são Stream em java?

Streams em java, são como esteiras de uma fábrica. Na esteira temos vários objetos passando por ela, porém ela não guarda esses objetos. Uma Stream percorre os objetos de forma simples, sem precisar utilizar loops complexos, e consegue realizar diversas operaões com esses objetos.

Vejamos abaixo, um exemplo de função para retornar apenas os numeros pares de uma lista, utilizando o for tradicional e depois utilizando stream.

### Com FOR tradicional

```
 List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6);

for(int i = 0;  i < numeros.size(); i++){
  int n = numeros.get(i);
  if(n % 2 == 0){
     System.out.println(n);
  }
  
}

```
### Com STREAM

```
List<Integer> numeros = Arrays.asList(1, 2, 3, 4, 5, 6);

        numeros.stream()
               .filter(n -> n % 2 == 0) // Aqui se diz que para cada numero n (n ->), retorne apenas se n/% for igual a 0
               .forEach(System.out::println); // imprime cada um
    

```

## Resumindo...

<img src="images/stream.png" alt="Stream" width="300">


Imagine que numeros é uma fila de caixinhas com números dentro:

📦 [1] [2] [3] [4] [5] [6]

Quando você faz **numeros.stream()** você coloca essa fila numa **esteira de fábrica** (a stream).

Depois vem o **.filter(n -> n % 2 == 0)**: Aqui o Java vai pegar cada caixinha da esteira (cada número), chamar ela de n, e testar se é par.



