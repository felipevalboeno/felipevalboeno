# 🌿 SOLID

---


> 🟠  Single Responsibility Principle (SRP)
    **Princípio da Responsabilidade Única:**

     Uma classe deve ter apenas um motivo para mudar, ou seja, ela deve ter apenas uma responsabilidade.


```
//exemplo ruim: Problema: A classe Relatorio tem duas responsabilidades: gerar relatório e salvar em arquivo.
class Relatorio {
    public void gerarRelatorio() {
        // gera relatório
    }

    public void salvarNoArquivo() {
        // salva relatório em arquivo
    }
}

//exemplo correto
class Relatorio {
    public void gerarRelatorio() {
        // gera relatório
    }
}

class RelatorioArquivo {
    public void salvar(Relatorio relatorio) {
        // salva relatório em arquivo
    }
}
//Cada classe tem uma única responsabilidade: gerar ou salvar.

```
---

> Open/Closed Principle (OCP)
    🟠 **Princípio Aberto/Fechado:**
        
     Uma classe deve estar aberta para extensão, mas fechada para modificação.

```
//exemplo ruim: Toda vez que você quiser adicionar uma operação nova, precisa modificar a classe.
class Calculadora {
    public double calcular(String tipo, double a, double b) {
        if (tipo.equals("SOMA")) return a + b;
        else if (tipo.equals("MULT")) return a * b;
        return 0;
    }
}

//exemplo correto:
interface Operacao {
    double calcular(double a, double b);
}

class Soma implements Operacao {
    public double calcular(double a, double b) {
        return a + b;
    }
}

class Multiplicacao implements Operacao {
    public double calcular(double a, double b) {
        return a * b;
    }
}

class Calculadora {
    public double calcular(Operacao operacao, double a, double b) {
        return operacao.calcular(a, b);
    }
}
Agora, para adicionar uma nova operação, basta criar uma nova classe que implemente Operacao, sem modificar a Calculadora.

```

---

> Liskov Substitution Principle (LSP)
    🟠 **Princípio da Substituição de Liskov:**
     
     Classes derivadas devem poder ser substituídas por suas classes base sem quebrar o funcionamento do programa.

```
Exemplo ruim:Pinguim não pode substituir Ave porque lança exceção ao chamar voar().

class Ave {
    public void voar() {}
}

class Pinguim extends Ave {
    public void voar() {
        throw new UnsupportedOperationException("Pinguins não voam!");
    }
}

Exemplo correto: 

interface Ave {
}

interface AveQueVoa {
    void voar();
}

class Pardal implements AveQueVoa {
    public void voar() {
        System.out.println("Pardal voando");
    }
}

class Pinguim implements Ave {
    // Pinguim não implementa AveQueVoa
}

//Cada classe implementa apenas o que faz sentido, evitando violações do LSP.

```
---

> Interface Segregation Principle (ISP)
    🟠 **Princípio da Segregação de Interfaces:**
    
     Muitas interfaces específicas são melhores que uma interface única e genérica.

```
Exemplo ruim: Robô não tira férias, mas é forçado a implementar.
interface Trabalhador {
    void trabalhar();
    void tirarFerias();
}

class Funcionario implements Trabalhador {
    public void trabalhar() { }
    public void tirarFerias() { }
}

class Robo implements Trabalhador {
    public void trabalhar() { }
    public void tirarFerias() {
        throw new UnsupportedOperationException();
    }
}

Exemplo correto: 
interface Trabalhador {
    void trabalhar();
}

interface Ferias {
    void tirarFerias();
}

class Funcionario implements Trabalhador, Ferias {
    public void trabalhar() { }
    public void tirarFerias() { }
}

class Robo implements Trabalhador {
    public void trabalhar() { }
}

//Agora as classes implementam apenas o que é relevante.

```
---

> Dependency Inversion Principle (DIP)
    🟠 **Princípio da Inversão de Dependência:**
    
     Dependa de abstrações, não de implementações concretas.

```
Exemplo ruim: UsuarioService depende de uma implementação concreta (MySQLDatabase).
class MySQLDatabase {
    public void salvar() {}
}

class UsuarioService {
    private MySQLDatabase db = new MySQLDatabase();

    public void salvarUsuario() {
        db.salvar();
    }
}
// Exemplo correto: UsuarioService agora depende de uma abstração (Database) e não de uma implementação concreta.

interface Database {
    void salvar();
}

class MySQLDatabase implements Database {
    public void salvar() {}
}

class UsuarioService {
    private Database db;

    public UsuarioService(Database db) {
        this.db = db;
    }

    public void salvarUsuario() {
        db.salvar();
    }
}

// Uso
Database db = new MySQLDatabase();
UsuarioService service = new UsuarioService(db);
service.salvarUsuario();

```
---

## Princípio X Objetivo

- **SRP**	Uma classe = uma responsabilidade
- **OCP**	Aberta para extensão, fechada para modificação
- **LSP**	Subclasses podem substituir a superclasse
- **ISP**	Interfaces específicas > interface única gigante
- **DIP**	Dependa de abstrações, não de concretos