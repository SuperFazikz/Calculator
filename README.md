# Calculator
import java.util.Scanner;

public class Main {
    
    public static double getNumber(){ // Метод отвечает за ввод числа, тут проверяется чтобы число было в значении int иначе надо будет ввести его снова
        Scanner scan = new Scanner(System.in); // Для создания самого объекта Scanner в его конструктор передается объект System.in. 
        System.out.println("Введите пожалуйста число:\n" );
        if(scan.hasNextDouble()){  // Проверяется, если было введено число 
            return scan.nextDouble(); // возвращается число
        } else {
            System.out.println("Написано чтобы ввели число, а вы ввели какую-то херню! Давай по новой!\n" );
            return getNumber();
        }
    }
    
    public static char getOperation(){ // Метод отвечает за выбор операции. Пользователь вводит число, отвечающее операции и программа проверяет какое он ввел число
         Scanner scan = new Scanner(System.in);
         System.out.println("Выбери операцию уеба:\n1 - Сложение\n2 - Вычитание\n3 - Умножение\n4 - Деление\n5 - Возведение в степень\n6 - Возврат квадратного корня");
         int countOperationNumber = 0; // 
         if(scan.hasNextInt()){
            countOperationNumber = scan.nextInt();
         } else {
            System.out.println("Гандонио, надо чтобы ты ввел число, а ты ввел какую-то херню! Давай по новой!\n" );
            return getOperation();
         }
         
         switch(countOperationNumber){
            case 1:
                return '+';
            case 2:
                return '-';
            case 3:
                return '*';
            case 4:
                return '/';
            case 5:
                return '^';
            case 6:
                return '√';
            default:
                System.out.println("ты че падла, надо чтобы ты ввел число, а ты ввел какую-то херню! Давай по новой!\n" );
                return getOperation();
         }
         
    }
    
    public static double sum(double num1, double num2){
        return num1 + num2;
    }
    
    public static double raz(double num1, double num2){
        return num1 - num2;
    }
    
    public static double umn(double num1, double num2){
        return num1 * num2;
    }
    
    public static double del(double num1, double num2){
        if(num2 != 0){
            return num1 / num2;
        } else {
            System.out.println("Пидор, на ноль делить нельзя. Лови краш\n" );
            return 0;
        }
    }
    
    public static double step(double x, double y){
        double c = 1;
        if(y == 0){
            c = 1;
        } else if(y == 1){
            c = x;
        } else if(y > 1){
            while (y != 0){
                c *= x;
                y--;
            }
        } else if(y < 0){
            while(y != 0){
                c *= (1 / x);
                y++;
            }
        }
        return c;
    }
    
    public static double square(double x){
        return Math.sqrt(x);
    }
    
    public static double calc(double x, double y, char operation){
        switch(operation){
            case '+':
                return sum(x, y);
            case '-':
                return raz(x, y);
            case '*':
                return umn(x, y);
            case '/':
                return del(x, y);
            case '^':
                return step(x, y);
            case '√':
                return square(x);
            default:
                return 0;
        }
    }
    
	public static void main(String[] args) {
		double a = getNumber();
		double b = getNumber();
		char c = getOperation();
		double result = calc(a, b, c);
		System.out.println("Лови уеба: " + result);
	}
}
