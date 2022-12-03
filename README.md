import java.util.Scanner;

public class Main {

    //Ask user to Input pin if pin is not valid program will terminate if pin is valid program will proced to menu
    private static int getpin() {
        int actualPIN = 123456;
        int attempts = 3 ;
        int pin;
        do{
            System.out.println("Your attemps " +attempts +"\nEnter your pin : ");
            Scanner in=new Scanner(System.in);
            pin = in.nextInt();
            attempts--;  // number of attempts
        }while(pin != actualPIN && attempts > 0);

        if (pin == actualPIN)
            System.out.println("Acces granted");
        else{
            System.out.println("You have succed the maximum try\nAcces denied");
            System.exit(0);
        }
        return pin;
    }//end of pin method

    static Scanner input = new Scanner(System.in);

    public static void main(String args[] ) {
        double balance = 50000;

        getpin();//get user to input pin

        //simulating the ATM
        while(true) {
            //show the available possible options
            showMenu();
            int n = input.nextInt();
            switch(n) {
                case 1:
                    //withdraw from ATM
                    balance = withdrawMoney(balance);
                    break;

                case 2:
                    //deposit in ATM
                    balance = depositMoney(balance);
                    break;

                case 3:
                    //balance check
                    System.out.println("Available Balance: $"+balance);
                    break;

                case 4:
                    input.close();
                    System.exit(0);

                default:
                    System.out.println("Invalid selection. Please try again!!");
            }
            System.out.println("\n\n");
        }
    }

    /**
     * Method to show the possible options in the menu
     */
    private static void showMenu() {
        System.out.println("______________Automated Teller Machine_________________\nEnter \n\t1 to Withdraw Money\n\t2 to Deposit Money \n\t3 to Check Balance\n\t4 to EXIT\nEnter your choice: ");
    }

    /**
     Method to withdraw the amount
     */
    private static double withdrawMoney(double balance) {
        System.out.print("Enter money to be withdrawn: $");
        double withdraw = input.nextDouble();
        //check sufficient balance available

        if(balance >= withdraw) {
            balance -= withdraw;
            System.out.println("Please collect your money\nYour current balance is:  "+balance);
        }
        else
            System.out.println("Insufficient Balance");

        return balance;
    }

    /**
     Method to deposit the amount in ATM
     */
    private static double depositMoney(double balance) {

            System.out.print("Enter money to be deposited: $");

        double deposit = input.nextDouble();
            if(deposit > 0){
                balance += deposit;
                System.out.println("Your Money has been successfully deposited");
            }
            if (deposit <= 0) {
                System.out.println("Invalid value. Only Positive value can be deposited!!\nYour current balance is:  " + balance);
            }


        return balance;
}
}

