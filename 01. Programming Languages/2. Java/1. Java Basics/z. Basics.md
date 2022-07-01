###### main function

`main` function has a strict declaration
```
public static void main(String[] args) {
```

The main method of a class, if declared exactly as shown, is executed when you run the class as an application.

main's `args` contains program's arguments from the command line with which it was invoked.

###### Compiling and Running from Shell
<br>

`javac TestCode.java` - To compile a Java file into bytecode

`java TestCode.java` - To run a Java file. However first the code must be compiled.

Anytime the code is changed, it should be compiled again.

###### Getting user input (Scanner)

```
import java.util.Scanner;

Scanner input = new Scanner(System.in);
netflixCharge = input.nextDouble();
System.out.println(netflixCharge);
```

`System.out.println` is what is used for printing to console.

###### Loops

```
for (int fooFor = 0; fooFor < 4; fooFor++) {
    System.out.println(fooFor);
}

outer:
for (int i = 0; i < 2; i++) {
    for (int j = 0; j < 3; j++) {
        if (i == 1 && j == 1) {
            break outer;
            // breaks out of outer loop instead of only the inner one
        }
        System.out.println("Gets in");
    }
}

int[] fooList = {4, 5, 6, 7};
for (int bar : fooList) {
    System.out.println(bar);
}
```
