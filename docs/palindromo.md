# <span style="color:green;">💼 **Palindromo**</span>

> O que é um Palindromo?
Palindromo é uma palavra que ao ser lida ao contratio, forma a mesma palavra. Ou seja, uma palvra que pode ser lida da esquerda pra direita ou vice-versa.

Exemplos em java:

```
String texto = "ana";
texto = texto.toLowerCase();
   char[] letras = texto.toCharArray();
    
   boolean palindromo = true;
    
    for (int i = 0, j = letras.length -1; i < j; i++, j--){
      if (letras[i] != letras[j]){
        
        palindromo = false;
        break;
      }
    }
if(palindromo){
System.out.println("É palindromo");
  }else {
  System.out.println("Não é palindromo");
}


```


```
String str = "Radar";
str = str.toUpperCase();
        boolean isPalindrome = str.equals(new StringBuilder(str).reverse().toString());
        System.out.println(isPalindrome);

```


```
//tratando caso a palavra contenha letra maipuscula
 String texto = "Arara";

texto = texto.toUpperCase();

String inverso = new StringBuilder(texto).reverse().toString();

if(texto.equals(inverso)){
  System.out.println("É palindromo");
}else{
  
  System.out.println("Não é palindromo");
}
 

```




```
//criando palindromo utilizando método pilha 
import java.util.Stack;

public class Main {

    public static void main(String[] args) {
        System.out.println("Iniciando teste de palíndromo...\n");

        imprimeResultadoPalavra("ADA");
        imprimeResultadoPalavra("ABCD");
        imprimeResultadoPalavra("Ovovo");

        System.out.println("\nFim da execução.");
    }

    public static void imprimeResultadoPalavra(String palavra) {
        System.out.println(palavra + " é palíndromo? " + testaPalindromo(palavra));
    }

    public static boolean testaPalindromo(String palavra) {
        Stack<Character> pilha = new Stack<>();

        for (int i = 0; i < palavra.length(); i++) {
            pilha.add(palavra.charAt(i));
        }

        String palavraInversa = "";

        while (!pilha.isEmpty()) {
            palavraInversa += pilha.pop();
        }

        return palavraInversa.equalsIgnoreCase(palavra);
    }
}



```


```
//tratando caso a palavra contenha espaços

String texto = "A rar  a";
texto = texto.replaceAll("\\s+", "").toLowerCase();


String inverso = new StringBuilder(texto).reverse().toString();

if(texto.equals(inverso)){
  System.out.println("É palindromo");
}else{
  
  System.out.println("Não é palindromo");
}
 

```



```
// Tratando caso a palavra contenha acentuações

 String texto = "á raR  a";


texto = Normalizer
          .normalize(texto, Normalizer.Form.NFD)
          .replaceAll("[^\\p{ASCII}]", "") // remove acentos
          .replaceAll("[^a-zA-Z0-9]", "")  // remove espaços e pontuação
          .toLowerCase();

String inverso = new StringBuilder(texto).reverse().toString();

if(texto.equals(inverso)){
  System.out.println("É palindromo");
}else{
  
  System.out.println("Não é palindromo");
}
 

```




