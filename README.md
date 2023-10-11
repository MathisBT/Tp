import java.util.Random;
import java.util.Scanner;

public class Main {
    public Main() {
    }

    public static void main(String[] args) {
        int difficultyChoice = 0;
        int lowerBound = 0;
        int upperBound = 0;
        int tryAmounts = 0;

        Scanner scan = new Scanner(System.in);

        //choisir une difficulté
        do {
            System.out.println("1. Facile: Nombre entre 1 et 19, 10 essais");
            System.out.println("2. Normal: Nombre entre 1 et 49, 5 essais");
            System.out.println("3. Difficile: Nombre entre 1 et 99, 5 essais");
            System.out.println("4. Impossible: Nombre entre 1 et 999, 1 essai");

            difficultyChoice = scan.nextInt();

            switch (difficultyChoice) {
                case 1:
                    System.out.println("Vous avez choisis facile");
                    upperBound = 20;
                    tryAmounts = 10;
                    break;
                case 2:
                    System.out.println("Vous avez choisis normal");
                    upperBound = 50;
                    tryAmounts = 5;
                    break;
                case 3:
                    System.out.println("Vous avez choisis difficile");
                    upperBound = 100;
                    tryAmounts = 5;
                    break;
                case 4:
                    System.out.println("Vous avez choisis impossible");
                    upperBound = 1000;
                    tryAmounts = 1;
                    break;
                default:
                    System.out.println("Le chiffre doit etre compris entre 1 et 4");
                    break;
            }
        } while(difficultyChoice < 1 || difficultyChoice > 4);

        //générer un nombre aléatoire
        Random r = new Random();
        int generatedNumber = r.nextInt(1, upperBound);
        int numberChoice = 0;
        int tries = 0;


        do {
            System.out.print("(" + (tries + 1) + "/" + tryAmounts + ") 0 < ? < " + upperBound + " : ");
            numberChoice = scan.nextInt();
            ++tries;
        } while(generatedNumber != numberChoice && tries != tryAmounts);

        if (generatedNumber == numberChoice) {
            System.out.println("Félicitation");
        } else {
            System.out.println("Vous avez échoué");
            System.out.println("le nombre mystere etait:" + generatedNumber);
        }

    }
}
