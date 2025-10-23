# <span style="color:green;">💼 **@Transactional**</span>

> Pra que serve o @Transactional?

A anotação @Transactional serve para controlar transações de banco de dados de forma automática.

Ou seja, ela garante que um bloco de operações SQL (ou JPA):

-   só será confirmado (commit) se tudo der certo,

-   e será desfeito (rollback) se alguma exceção acontecer.

Exemplo:

```
@Service
public class ContaService {

    @Autowired
    private ContaRepository repository;

    @Transactional
    public void transferir(Long origemId, Long destinoId, double valor) {

        Conta origem = repository.findById(origemId).orElseThrow();
        Conta destino = repository.findById(destinoId).orElseThrow();

        origem.setSaldo(origem.getSaldo() - valor);
        destino.setSaldo(destino.getSaldo() + valor);

        repository.save(origem);
        repository.save(destino);

        // Se der erro aqui, tudo é desfeito (rollback)
    }
}


```

-   Se tudo correr bem → o Spring faz COMMIT.

-   Se lançar uma exceção (ex: RuntimeException) → o Spring faz ROLLBACK automático, ou seja, nenhuma das alterações é gravada no banco.


É quase a mesma ideia do que usar o START TRANSACTION no MySql, por exemplo:

```
START TRANSACTION;

UPDATE conta SET saldo = saldo - 100 WHERE id = 1;
UPDATE conta SET saldo = saldo + 100 WHERE id = 2;

COMMIT;
```

Você tem o poder de desfazer essa transação antes do commit. O ideal é fazer o update, checar se deu tudo certo, e por fim dar um commit, mas se algo der errado dentro do bloco da transação, será feito um rollback automático de tudo dentro do bloco. Porém, sevocê commitou no final e ocorreu tudo bem, não é possível dar rollback mais.