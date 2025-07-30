import java.util.Scanner;
import java.io.BufferedReader;
import java.io.FileNotFoundException;
import java.io.FileReader;
import java.io.IOException;
import java.util.ArrayList;
import java.util.Random;

public class HangmanGame {
    public static void main(String[] args) {
     
    // Aqui foi criado o algoritmo que vai pegar a lista de palavras e sortear uma aleatoriamente.
    // Foram utilizadas as classes ArrayList (lista de vetores, no caso as palavras.) e Random para o sorteio.
    String filePath = "words.txt";
    ArrayList<String> words = new ArrayList<>();

    try(BufferedReader reader = new BufferedReader(new FileReader(filePath))){
       String line;
       while((line = reader.readLine()) != null){
           words.add(line.trim());
    // O método "trim" evita que apareça algum espaçamento do arquivo de palavras "words.txt".       
       }
    }
    catch(FileNotFoundException e){
       System.out.println("Arquivo não encontrado.");
    }
    catch(IOException e){
        System.out.println("Algo deu errado.");
    }
    // Em caso de algum erro, o "catch" identificará o problema e será mostrada uma mensagem de erro na tela.

    Random random = new Random();

    String word = words.get(random.nextInt(words.size()));
   // Esta linha é a parte que pega as palavras aleatoriamente, usando o método "size" para captar todas as palavras do "words.txt".

     Scanner scanner = new Scanner(System.in);
     
     ArrayList<Character> wordState = new ArrayList<>();

     int palpitesErrados = 0;
   // Aqui foi declarada a variável "palpitesErrados" para qualquer tentativa incorreta.
     for(int i = 0; i < word.length(); i++) {
        wordState.add('_');
     }
    // Ficará somando um segmento que está por vir.
      
      System.out.println("!¨¨¨¨¨¨¨¨¨✯¨¨¨¨¨¨¨¨¨✯¨¨¨¨¨!");
      System.out.println("! ❄Jogo da Forca em Java❄ !");
      System.out.println("!¨¨¨¨¨✯¨¨¨¨¨¨¨¨¨¨✯¨¨¨¨¨¨¨¨!");

    // Um loop que seguirá até atingir o limite de erros. (máximo: 6) 
      while(palpitesErrados < 6){
    // Ele vai resgatando o desenho atual, segundo o total de erros.
      System.out.print(getDesenhaPessoa(palpitesErrados));  
      System.out.print("Palavra: ");
      
      for(char c : wordState){
           System.out.print(c + " ");
      }
      System.out.println();
    // Até encerrar o jogo, mostrará "Palavra: _____" e "Dê um palpite:" que requisitará uma entrada de letra do usuário.
      System.out.println("Dê um palpite: ");
      char suposição = scanner.next().toLowerCase().charAt(0);
    // Se o palpite estiver correto, mostrará esta mensagem e seguirá o jogo.  
      if(word.indexOf(suposição) >= 0){
         System.out.println("Palpite correto!\n");
    // Os caracteres corretos são substituidos nos espaços de linha e acrescentados às letras da palavra secreta já desvendadas. 
         for(int i = 0; i < word.length(); i++){
             if(word.charAt(i) == suposição){
                  wordState.set(i, suposição);
                  } 

              }
    // Caso todos os espaços de caracter forem preenchidos, logo a pessoa já acertou a palavra e ganhou. O comando "break" é utilizado para interromper o laço de repetição principal.
    // Imprimirá na tela o estado atual do desenho da forca e qual era a palavra secreta.
              if(!wordState.contains('_')){
                   System.out.print(getDesenhaPessoa(palpitesErrados));
                   System.out.println("Ganhou :D");
                   System.out.println("A palavra era: " + word);
                   break;
              }
      }
    // Caso o palpite esteja errado, será somado às tentativas prévias incorretas e impressa esta mensagem.  
      else{
           palpitesErrados++;
           System.out.println("Palpite incorreto!\n");
       }        
      }
    // Caso o número de palpites incorretos ultrapasse 5, o jogo acaba e é revelada a palavra secreta, junto ao desenho inteiro da forca.
      if(palpitesErrados >= 6){
          System.out.print(getDesenhaPessoa(palpitesErrados));
          System.out.println("Acabou o jogo :(");
          System.out.println("A palavra era: " + word);
      }
      
      
      scanner.close();
     
    }
    // Aqui fica a etapa do desenho do personagem palito clássico, para ficar mais lúdico.
    // Basicamente, a cada erro será acrescentado um destes casos, até encerrar o jogo.
    // OBS.: São usados "\\" pois se usasse apenas 1, seria interpretado como uma sequência de escape.
    static String getDesenhaPessoa(int palpitesErrados){

         return switch(palpitesErrados){
               case 0 -> """
                       
                       
                         
                         """;
               case 1 -> """
                          O
                       
                         
                         """;
               case 2 -> """
                          O
                          |
                         
                         """;
               case 3 -> """
                          O
                         /|
                         
                         """;
               case 4 -> """
                          O
                         /|\\
                         
                         """;
               case 5 -> """
                          O
                         /|\\
                         /
                         """;
               case 6 -> """
                          O
                         /|\\
                         / \\
                         """;                                                                                                                                                      
               default -> "";

         };

    }
}
