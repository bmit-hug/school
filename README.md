# Lernportfolio
## 2023-11-23
### [To do-Liste](ToDoList.java)

~~~~java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class ToDoList {

    //Erstelle Objekte "input" und "toDoList"
    static Scanner input = new Scanner(System.in);
    static List<String> toDoList = new ArrayList<>();

    //Element zur Liste hinzufügen
    public static void addToList() {

            System.out.println("Add element: ");
            String addElement = input.nextLine();
            toDoList.add(addElement);

            System.out.println("successfully added " + addElement);
            askForInput();
        }
    
    //Element von der Liste entfernen
    public static void removeFromList() {

        System.out.println("Remove element: ");
        String removeElement = input.nextLine();

        //Überprüfen of das zu enfernende Element in der Liste existiert
        if (toDoList.contains(removeElement)) {
            toDoList.remove(removeElement);

            System.out.println("successfully removed" + removeElement);
            askForInput();

        } else {
            System.out.println("Error, element not found");
            removeFromList();
        }
    }

    //Element in der Liste als "erledigt" markieren
    public static void markAsDone() {

        System.out.println("Mark element as done: ");
        String markElement = input.nextLine();

        if (toDoList.contains(markElement)) {

            //Hole den Index des Elements
            int indexOfElement = toDoList.indexOf(markElement);

            //Hole das Element des Indexes
            String elementOfIndex = toDoList.get(indexOfElement);

            //Füge dem Element in der Liste ein Stern hinzu
            toDoList.set(indexOfElement, elementOfIndex + " *");
            System.out.println("successfully marked" + markElement + "as done");
            askForInput();

        } else {
            System.out.println("Error, element not found");
            removeFromList();
        }
    }

    //Alle Elemente der Liste anzeigen
    public static void showList() {

        //Initialisiere einen Zähler um die Liste geordnet anzuzueigen
        int count = 1;
        System.out.println("");

        //Durchlaufe jedes Element und zeige es an
        for (String element : toDoList) {
            System.out.println(count + ". " + element);
            count += 1;
        }

        System.out.println("");
        askForInput();
    }

    //Eingaben vom Nutzer fordern
    public static void askForInput() {

        System.out.println("(1) add\n(2) remove\n(3) mark\n(4) show\n");
        String userInput = input.nextLine();

        /*
        Die Eingabe des Nutzers abfragen (Da in hier jeder Fall
        auf die gleiche Bedingung abgefragt wird, benutzen wir
        einen "switch" anstatt wie üblich "if", "elseif" oder "else".)
        */

        switch (userInput) {
            case "1":
                addToList();
                break;
            
            case "2":
                removeFromList();
                break;
            
            case "3":
                markAsDone();
                break;

            case "4":
                showList();
                break;
        
            default:
                System.out.println("ERROR");
                askForInput();
                break;
        }
    }

    public static void main(String[] args) {
        askForInput();
    }
}
~~~~

## 2023-10-26
### [Schaltjahr](Schaltjahr.java)

~~~~java
import java.util.Scanner;

public class Schaltjahr {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        System.out.println("\nJahr:");
        int year = input.nextInt();
        input.nextLine();
        input.close();

        boolean isLeapYear = false;

        // Überprüft ob das eingegebene Jahr durch 4 teilbar ist
        if (year % 4 == 0) {
            isLeapYear = true;

            // Überprüft ob das eingegebene Jahr durch 100 teilbar ist
            if (year % 100 == 0) {
                isLeapYear = false;

                // Überprüft ob das eingegebene Jahr durch 400 teilbar ist
                if (year % 400 == 0) {
                    isLeapYear = true;
                }
            }
        }

        if (isLeapYear) {
            System.out.println(year + " ist ein Schaltjahr");
        } else {
            System.out.println(year + " ist kein Schaltjahr");
        }
    }
}
~~~~

## Erklärung:

~~~~java
if (year % 4 == 0) {
    isLeapYear = false;
}
~~~~
Der Modulo Operator `%` wird benutzt um zu überprüfen ob das Resultat von `year` geteilt durch 4 eine gerade Zahl ist.

***

## 2023-09-28
### [Einfacher Java Taschenrechner](calculator.java)

~~~~java
import java.util.Scanner;

public class Calculator {
    public static void main(String[] args) {
        Scanner input = new Scanner(System.in);

        // Fragt den Benutzer nach der ersten Zahl
        System.out.println("\nZahl 1:");
        int num1 = input.nextInt();
        input.nextLine();

        // Fragt den Benutzer nach dem Operationszeichen
        System.out.println("\nOperationszeichen:");
        String operator = input.nextLine();
        
        // Fragt den Benutzer nach der ersten Zahl
        System.out.println("\nZahl 2:");
        int num2 = input.nextInt();
        input.close();

        // Ausgabe der beiden Zahlen mit dem "+" Operationszeichen
        if (operator.equals("+")) {
            System.out.println("\nResultat:\n" +  (num1 + num2) + "\n");
        }

        // Ausgabe der beiden Zahlen mit dem "-" Operationszeichen
        else if (operator.equals("-")) {
            System.out.println("\nResultat:\n" +  (num1 - num2) + "\n");
        }

        // Ausgabe der beiden Zahlen mit dem "*" Operationszeichen
        else if (operator.equals("*")) {
            System.out.println("\nResultat:\n" +  (num1 * num2) + "\n");
        }

        // Ausgabe der beiden Zahlen mit dem "/" Operationszeichen
        else if (operator.equals("/")) {
            System.out.println("\nResultat:\n" +  (num1 / num2) + "\n");
        }
    }
}
~~~~

## Erklärung:

~~~~java
import java.util.Scanner;
~~~~

> Importiert die Scanner-Klasse aus dem `Java.util` -Paket. Der Scanner wird verwendet, um Benutzereingaben (Inputs) von der Konsole zu lesen.

~~~~java
public class Calculator {
~~~~
 > Hier wird eine öffentliche Klasse mit dem Namen "Calculator" deklariert. Dies ist die Hauptklasse des Programms.

~~~~java
public static void main(String[] args) {
~~~~
> Dies ist die main-Methode des Programms, die den Einstiegspunkt für die Ausführung darstellt. Sie hat ein `String[] args` -Parameter, der dazu verwendet werden kann, Befehlszeilenargumente zu übergeben, wird in diesem Fall jedoch nicht verwendet.

~~~~java
Scanner scanner = new Scanner(System.in);
~~~~
> In dieser Zeile wird eine Instanz der Scanner-Klasse mit dem Namen "scanner" erstellt. Der Scanner wird mit System.in initialisiert, was bedeutet, dass er auf die Standard-Eingabe (die Konsole) zugreift, um Benutzereingaben zu lesen.

~~~~java
System.out.println("\nZahl 1:");
~~~~
> Diese Zeile gibt den Text "Zahl 1:" in die Konsole aus, um den Benutzer zur Eingabe der ersten Zahl aufzufordern.

~~~~java
int x = scanner.nextInt();
~~~~
> Hier wird die Benutzereingabe für die erste Zahl eingelesen und in der Variablen `x` als Ganzzahl (int) gespeichert. `scanner.nextInt()` erwartet, dass der Benutzer eine Ganzzahl eingibt.

~~~~java
scanner.nextLine();
~~~~
> Diese Zeile wird verwendet, um den Zeilenumbruch (newline character) nach der vorherigen Eingabe zu verarbeiten und sicherzustellen, dass die nächste Eingabe nicht von der vorherigen Zeile beeinflusst wird.

~~~~java
System.out.println("\nOperator:");
~~~~
> Hier wird der Benutzer aufgefordert, einen Operator einzugeben, der die gewünschte mathematische Operation darstellt.

~~~~java
String y = scanner.nextLine();
~~~~
> Die Benutzereingabe für den Operator wird in der Variable `y` als Zeichenkette (String) gespeichert. `scanner.nextLine()` liest eine gesamte Zeile aus der Konsole, einschließlich des Zeilenumbruchs.

~~~~java
System.out.println("\nZahl 2:");
~~~~
> Der Benutzer wird aufgefordert, die zweite Zahl einzugeben.

~~~~java
int z = scanner.nextInt();
~~~~
> Die Benutzereingabe für die zweite Zahl wird in der Variablen `z` als Ganzzahl gespeichert.

~~~~java
scanner.close();
~~~~
> Der Scanner wird geschlossen, um Ressourcen freizugeben und die Eingabe von der Konsole zu beenden.

~~~~java
String res_msg = "\nResultat:";
~~~~
> Eine Zeichenkette `res_msg` wird erstellt, um das Präfix für die Ausgabe des Ergebnisses zu speichern.

~~~~java
if (y.equals("+")) {
    System.out.println(res_msg + "\n" +  (x + z) + "\n");
}
else if (y.equals("-")) {
    System.out.println(res_msg + "\n" +  (x - z) + "\n");
}
else if (y.equals("/")) {
    System.out.println(res_msg + "\n" +  (x / z) + "\n");
}
else if (y.equals("*")) {
    System.out.println(res_msg + "\n" +  (x * z) + "\n");
}
~~~~
> In den obrigen `if-else if`-Blöcken wird der eingegebene Operator `y` überprüft, und je nachdem, welcher Operator eingegeben wurde (`+`, `-`, `/`, `*`), wird die entsprechende mathematische Operation auf den beiden eingegebenen Zahlen `x` und `z` durchgeführt. Das Ergebnis wird dann auf die Konsole ausgegeben, zusammen mit dem Präfix `res_msg`.
