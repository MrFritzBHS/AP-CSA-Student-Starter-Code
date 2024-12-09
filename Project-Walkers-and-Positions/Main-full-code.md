# Main class - complete code 

Full code - you don't build it

Copy and paste **EVERYTHING** below and replace the ENTIRE Main class in the Walkers and Positions Main class


```java
import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        // Opening prompt
        System.out.println("\n\n>>> Welcome to the game: ~Two Walkers~");
        System.out.println(">>> Both players begin at the same starting position");
        System.out.println(">>> and they each walk in one direction");
        System.out.println(">>> each turn.");
        System.out.println(">>> the closest to (0, 0) after 5 walks wins!");
        System.out.println("\n\n");

        // make one common starting point
        int startingX = (int) (Math.random() * 22) - 11;
        int startingY = (int) (Math.random() * 22) - 11;
        Position startingPoint = new Position(startingX, startingY);

        // make two walkers starting at the common starting point
        System.out.print("What is the name of the first walker? ");
        String name = input.nextLine();
        Walker walker1 = new Walker(name, startingPoint);

        System.out.print("What is the name of the second walker? ");
        name = input.nextLine();
        Walker walker2 = new Walker(name, startingPoint);

        // Print starting summary
        System.out.println("\n### Starting summary ###");
        System.out.println("\t" + walker1);
        System.out.println("\t" + walker2);

        // both walkers take walks 5 times
        for (int i = 0; i < 5; i++) {
            // Walker 1 turn
            System.out.println("\n-----" + walker1.getName() + "-----");
            System.out.print("\tChoose Direction: N, S, E, W: ");
            String direction = input.nextLine();
            // move walker
            walker1.move(direction.toUpperCase());

            // Walker 2 turn
            System.out.println("\n-----" + walker2.getName() + "-----");
            System.out.print("\tChoose Direction: N, S, E, W: ");
            direction = input.nextLine();
            // move walker
            walker2.move(direction.toUpperCase());

            // Round summary
            System.out.println("\n### After " + (i+1) + " walks ###");
            System.out.println(walker1);
            System.out.println(walker2);
            if(walker1.getPosition()
                .equals(walker2.getPosition())) {
                    System.out.println("That's the same spot!");
                }
        }

        System.out.println("\n\t~~~ Game Over ~~~");
        if (walker1.closerToHome(walker2)) {
            System.out.println(walker1.getName() + " is closest to home!");
        }
        else if (walker2.closerToHome(walker1)) {
            System.out.println(walker2.getName() + " is closest to home!");
        }
        else {
            System.out.print(walker1.getName() + " and " + walker2.getName() + " are equally distant from home!");
        }

        input.close();
    }
}
```
