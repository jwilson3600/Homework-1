# Homework 1

**Name: Jacob Wilson**

## 1. Character Values

This program prints the numeric value of each character in the name Jacob.

```java
class hw1 {
    public static void main(String[] args) {
        String s = "Jacob";

        for (Character c : s.toCharArray()) {
            System.out.println((int) c);
        }
    }
}
```

### Output

```text
74
97
99
111
98
```

## 2. Number-Base Converter

This program converts a number to binary, decimal, octal, and hexadecimal.

```java
import java.util.Scanner;

public class BaseConverter {
    public static void main(String[] args) {
        Scanner scan = new Scanner(System.in);

        System.out.print("Enter a number: ");
        String number = scan.next();

        System.out.print("Enter the base (2, 8, 10, or 16): ");
        int base = scan.nextInt();

        int decimal = Integer.parseInt(number, base);

        System.out.println("Binary: "
                + Integer.toString(decimal, 2));
        System.out.println("Decimal: " + decimal);
        System.out.println("Octal: "
                + Integer.toString(decimal, 8));
        System.out.println("Hexadecimal: "
                + Integer.toString(decimal, 16));
    }
}
```

### Output

```text
Enter a number: 10
Enter the base (2, 8, 10, or 16): 10
Binary: 1010
Decimal: 10
Octal: 12
Hexadecimal: a
```

## 3. Image-to-Pixel Converter

This program reads `smiley.png` and writes its pixel colors to `output.txt`.

```java
import java.awt.Color;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;
import java.io.PrintWriter;
import javax.imageio.ImageIO;

public class hw1pix {
    public static String convert(Color color) {
        int red = color.getRed();
        int green = color.getGreen();
        int blue = color.getBlue();

        if (red == 237 && green == 28 && blue == 36) {
            return "R";
        } else if (red == 0 && green == 0 && blue == 0) {
            return "B";
        } else if (red == 255 && green == 242 && blue == 0) {
            return "Y";
        } else {
            return "(" + red + ", " + green + ", " + blue + ")";
        }
    }

    public static void main(String[] args) throws IOException {
        PrintWriter outputFile =
                new PrintWriter("output.txt");

        BufferedImage imageFile =
                ImageIO.read(new File("./smiley.png"));

        int width = imageFile.getWidth();
        int height = imageFile.getHeight();

        for (int y = 0; y < height; y++) {
            for (int x = 0; x < width; x++) {
                Color color =
                        new Color(imageFile.getRGB(x, y));

                String convertedColor = convert(color);

                outputFile.print(convertedColor);
                outputFile.print(" ");
            }

            outputFile.println();
        }

        outputFile.close();
    }
}
```

### Output

```text
R R R R R R R R R R R
R B B B B B B B B B R
R B Y Y Y Y Y Y Y B R
R B Y B Y Y Y B Y B R
R B Y Y Y Y Y Y Y B R
R B Y Y Y B Y Y Y B R
R B Y B Y Y Y B Y B R
R B Y B B B B B Y B R
R B Y Y Y Y Y Y Y B R
R B B B B B B B B B R
R R R R R R R R R R R
```

## 4. Create an Image from Pixel Values

This program asks for red, green, and blue values and creates a 100-by-100 pixel image named `image.png`.

```java
import java.awt.Color;
import java.awt.image.BufferedImage;
import java.io.File;
import javax.imageio.ImageIO;
import java.util.Scanner;

public class CreateImage {
    public static void main(String[] args) throws Exception {
        Scanner scan = new Scanner(System.in);

        System.out.print("Enter red value (0-255): ");
        int red = scan.nextInt();

        System.out.print("Enter green value (0-255): ");
        int green = scan.nextInt();

        System.out.print("Enter blue value (0-255): ");
        int blue = scan.nextInt();

        BufferedImage image = new BufferedImage(
                100, 100, BufferedImage.TYPE_INT_RGB);

        Color color = new Color(red, green, blue);

        for (int x = 0; x < 100; x++) {
            for (int y = 0; y < 100; y++) {
                image.setRGB(x, y, color.getRGB());
            }
        }

        ImageIO.write(
                image, "png", new File("image.png"));

        System.out.println("Image created!");
    }
}
```

### Output

```text
Enter red value (0-255): 255
Enter green value (0-255): 0
Enter blue value (0-255): 0
Image created!
```

The program creates a solid red image.


## 5. Boundary Tests

This program tests zero, the largest 32-bit unsigned value, and a negative two's-complement value.

```java
public class BoundaryTest {
    public static void main(String[] args) {
        int zero = 0;
        long largestUnsigned = 4294967295L;
        int negative = -5;

        System.out.println("Zero: " + zero);

        System.out.println(
                "Largest unsigned value: "
                        + largestUnsigned);

        System.out.println(
                "Negative value: " + negative);

        System.out.println(
                "Negative in two's complement: "
                        + Integer.toBinaryString(negative));
    }
}
```

### Output

```text
Zero: 0
Largest unsigned value: 4294967295
Negative value: -5
Negative in two's complement: 11111111111111111111111111111011
```
