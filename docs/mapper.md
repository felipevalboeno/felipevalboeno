# <span style="color:green;">💼 **Model Mapper**</span>

> De onde veio o ModelMapper e pra que serve?

O ModelMapper, surgiu por volta de 2011. É uma biblioteca Java, criada pra facilitar o mapeamento entre objetos.
Se você vai trabalhar com entidades, DTO's, requests e reponses, vale a pena entender e considerar o uso dessa biblioteca, pois ela vai te livrar de adicionar campo a campo durante a criação de um objeto da entidade no DTO de response. Ou seja, te livra de fazer esse mapeamento manualmente. O ModelMapper tem cérebro, diferente do  BeanUtils.copyProperties, ele possui capacidades mais flexíveis como a conversão de variáveis, sendo uma ótima escolha para projetos maiores e mais complexos.

---

> Como utilizar o ModelMapper?

🟢 1- No seu projeto, o primeiro passo será adicionar a dependência dele no **pom.xml**

```
<dependency>
    <groupId>org.modelmapper</groupId>
    <artifactId>modelmapper</artifactId>
    <version>3.2.0</version>
</dependency>

```


🟢 2- Crie um Bean global para o ModelMapper, evitando criar uma nova instancia (mapper = new modelMapper()) em cada service.

```
@Configuration
public class AppConfig {

    @Bean
    public ModelMapper modelMapper() {
        return new ModelMapper();
    }
}

```
🟢 3- Agora, vamos supor que você tem um **Service**, que faz parte de um CRUD de animais, e você tem o método listar, para listar os animais cadstrados.


```
@Service
public class AnimalService {

    @Autowired
    private AnimalRepository repository;

    public List<AnimalResponse> listar() {
        List<AnimalEntity> entities = repository.findAll();
        List<AnimalResponse> response = new ArrayList<>();

        for (AnimalEntity e : entities) {
            AnimalResponse res = new AnimalResponse();

            // Mapeamento manual campo a campo
            res.setId(e.getId());
            res.setNome(e.getNome());
            res.setAniversario(e.getAniversario());
            res.setEspecie(e.getEspecie());
            res.setTutor(e.getTutor());

            response.add(res);
        }

        return response;
    }
}

```

Note que fazemos o mapeamento da response de forma manual, mas com o Model Mapper isso não é necessário.
Veja como fica usando o mapper abaixo:

```
@Service
public class AnimalService {

    @Autowired
    private AnimalRepository repository;

    @Autowired
    private ModelMapper mapper;

    // Listar todos os animais
    public List<AnimalResponse> listarAnimal() {
        return repository.findAll()
                .stream() 
                .map(entity -> mapper.map(entity, AnimalResponse.class)) 
                .collect(Collectors.toList()); 
    }

```
-   **return repository.findAll()** //Chama o método do Spring Data JPA que retorna todas as entidades AnimalEntity do banco

-   **map(entity -> mapper.map(entity, AnimalResponse.class))** //O map transforma cada elemento da stream em outro tipo, aqui transformamos cada AnimalEntity em um AnimalResponse

-   **.Stream() Converte essa lista em um Stream** — uma sequência de elementos que podem ser processados em cadeia.

Com isso, você pode aplicar operações como:

-   map() (transformar cada elemento)

-   filter() (filtrar por uma condição)

-   sorted() (ordenar)

-   collect() (juntar o resultado final)


-   **collect(Collectors.toList())** //Converte a Stream de AnimalResponse de volta para uma Lista normal (List<AnimalResponse>).


Ou como seria usando o BeanUtil:


```
@Service
public class AnimalService {


    @Autowired
    private AnimalRepository repository;

    public List<AnimalResponse> listarAnimal(){
        List<AnimalEntity> entities = repository.findAll();
        List<AnimalResponse> response = new ArrayList<>();

        for(AnimalEntity e : entities){
            AnimalResponse res = new AnimalResponse();
            BeanUtils.copyProperties(e, res);
            response.add(res);
        }

        return response;
    }

```

## Conclusão

Você pode e deve considerar utilizar o ModelMapper para mapeamento entre entidades em seus projetos dependendo do escopo deles.
Pesquise mais sobre essa biblioteca e facilite sua vida como desenvolvedor ;)
