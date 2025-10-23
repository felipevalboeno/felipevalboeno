# <span style="color:green;">💼 **Garbage Collector**</span>

> O que é o GarbageCollector?

O Garbage Collector é o coletor de lixo do Java. Surgiu na versão 1.0 de 1995. Um garbage(lixo) é qualquer objeto instanciado que não é usado mais pelo programa. 

🟢 Exempo:


```
String nome = new String("Felipe");
-> Criado o objeto Felipe na memória, do tipo String.

nome = new String("Ana");
-> A Variável nome passou a apontar para o objeto "Ana"

O objeto "Felipe" virou um garbage = lixo de memória.

```

O garbage collector (GC) é um processo automático do Java que roda em segundo plano. Ele encontra os objetos que não possuem mais referência, apaga eles, e reorganiza a memória pra evitar fragmentação.

Antes de excluir um objeto da memória, ele chama um método chamado finalize(). Vejamos um exemplo de como chamar o GC explicitamente. 


```
public class Main {

    static class Pessoa {
        private String nome;

        public Pessoa(String nome) {
            this.nome = nome;
        }

        // Método chamado pelo Garbage Collector ANTES de remover o objeto
        @Override
        protected void finalize() throws Throwable {
            System.out.println("🗑️ Objeto Pessoa \"" + nome + "\" foi coletado pelo Garbage Collector!");
        }
    }

    public static void main(String[] args) {
        System.out.println("🚀 Criando pessoas...");

        for (int i = 1; i <= 5; i++) {
            Pessoa p = new Pessoa("Pessoa " + i);
            // Depois do loop, 'p' será sobrescrita e os objetos antigos ficam sem referência
        }

        System.out.println("👋 Perdemos as referências para os objetos Pessoa.");
        System.out.println("💭 Sugerindo execução do Garbage Collector...\n");

        // Sugerimos a execução do GC
        System.gc();

        // Espera um pouco pra dar tempo do GC agir
        try {
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        System.out.println("\n✅ Programa finalizado!");
    }
}

```

A saída seria assim:

```
Criando pessoas...
Perdemos as referências para os objetos Pessoa.
Sugerindo execução do Garbage Collector...

Objeto Pessoa "Pessoa 5" foi coletado pelo Garbage Collector!
Objeto Pessoa "Pessoa 4" foi coletado pelo Garbage Collector!
Objeto Pessoa "Pessoa 3" foi coletado pelo Garbage Collector!
Objeto Pessoa "Pessoa 2" foi coletado pelo Garbage Collector!
Objeto Pessoa "Pessoa 1" foi coletado pelo Garbage Collector!

 Programa finalizado!

```
