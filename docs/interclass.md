# <span style="color:green;">💼 **Interface x Classe Abstrata**</span>

> Interface:

É como um contrato que define o que uma classe deve fazer, ou seja, quais métodos ela precisa implementar. Ela não contém a lógica de implementação dos métodos Interfaces permitem herança múltipla, então uma classe pode implementar várias interfaces ao mesmo tempo. Um bom exemplo de prática de Polimorfismo.

Como várias classes diferentes podem implementar a mesma interface, você consegue tratar objetos diferentes de forma uniforme → isso é polimorfismo.

Exemplo:

```
public interface ClienteRepository extends JpaRepository<Cliente, Long> {
}


```
Ao fazer isso, você está dizendo que essa interface vai trabalhar com a entidade Cliente e que o Spring deve fornecer as implementações prontas de acesso a dados (findAll, save, delete, etc.).

A interface não implementa nada por si só, mas define um contrato:

-   “Qualquer classe que usar essa interface vai ser capaz de fazer operações de banco para a entidade Cliente.”

-   O Spring cria uma implementação em tempo de execução automaticamente — você não precisa escrever SQL ou JDBC manualmente.


> Classe Abstrata:

Uma classe abstrata é uma classe que pode ter métodos abstratos (sem corpo) e métodos concretos (com implementação). Ela serve como modelo base para outras classes, permitindo compartilhar código comum. Diferente da interface, uma classe abstrata só pode ser estendida por uma única classe. Um bom exemplo de herança.

Uma classe abstrata serve como modelo base. Sendo chamada de superclasse, e quem a estende é chamada de subclasse.
Através da palavra super(), chamamos o construtor da superclasse.

```
public abstract class Animal {
    String nome;

    public void respirar() {
        System.out.println("Respirando...");
    }

    public abstract void emitirSom(); // método que obriga subclasses a implementar
}

```

```

public class Gato extends Animal {
    @Override
    public void emitirSom() {
        System.out.println("Miau!");
    }
}


```