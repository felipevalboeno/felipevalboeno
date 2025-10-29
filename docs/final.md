# <span style="color:green;">💼 **Quais as diferenças entre final, finally e finalize em Java?**</span>

> Finally

O finally é um bloco utilizado junto com tratamento de exceções como try e catch. Serve para executar um trecho que código, independende se vai dar erro ou não, e liberar recursos no final(como fechar conexões e arquivos). Visto isso, O bloco finally é muito usado para fechar conexões com banco de dados, arquivos, streams, ou qualquer recurso que precisa ser liberado manualmente.

**Exemplo do finally abaixo, de um trecho de método que faz leitura de arquivo:**

```
try {
    FileReader reader = new FileReader("dados.txt");
    // Lê o arquivo
} catch (IOException e) {
    System.out.println("Erro ao ler arquivo: " + e.getMessage());
} finally {
    System.out.println("Fechando recursos...");
    // Fecha o arquivo (se aberto)
}

```

**Exemplo do finally com conexão JDBC:**

```
Connection conn = null;
PreparedStatement stmt = null;
ResultSet rs = null;

try {
    conn = DriverManager.getConnection("jdbc:mysql://localhost/db", "user", "senha");
    stmt = conn.prepareStatement("SELECT * FROM cliente");
    rs = stmt.executeQuery();

    while (rs.next()) {
        System.out.println(rs.getString("nome"));
    }

} catch (SQLException e) {
    e.printStackTrace();

} finally {
    try {
        if (rs != null) rs.close();
        if (stmt != null) stmt.close();
        if (conn != null) conn.close();
        System.out.println("Conexão fechada com sucesso!");
    } catch (SQLException e) {
        e.printStackTrace();
    }
}


```

**Atenção!** - Desde o Java 7, surgiu o try-with-resources, que é uma forma mais moderna e limpa de fazer a mesma coisa — sem precisar do finally.


> Finalize

O finalize() é um método especial que o garbage collector chama antes de destruir um objeto, para permitir limpar recursos não gerenciados (como arquivos ou conexões nativas).

Mas **é obsoleto** (deprecated desde o Java 9 e removido no Java 18), porque:

-   O GC não garante quando (ou se) o finalize() será chamado.

-   Pode causar vazamentos de memória ou lentidão.

Exemplo do finalize:

```
@Override
protected void finalize() throws Throwable {
    System.out.println("Objeto sendo destruído...");
}

```

> final

É uma  Palavra-chave (modificador), que pode ser usado para variáveis, classes ou métodos.

-   final class: Não pode ser herdada.
-   final variable:  Não pode ter o valor alterado depois de atribuído.
-   final method: Não pode ser sobrescrito por subclasses.

Exemplo:

```
final int x = 10;   // valor fixo
final class Pessoa {}  // não pode ser herdada

```