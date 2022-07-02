     import java.util.Scanner;

    class Bank {
    private String accno;
    private String name;
    private long balance;

    Scanner Nakshatra = new Scanner(System.in);
    void openAccount() {
        System.out.print("Enter Account No: ");
        accno = Nakshatra.next();
        System.out.print("Enter Name: ");
        name = Nakshatra.next();
        System.out.print("Enter Balance: ");
        balance = Nakshatra.nextLong();
    }

    void showAccount() {
        System.out.println("\nAccount number: " + accno + "\nName: " + name + "\nBalance: " + balance + "\n");
    }

    void deposit() {
        long amt;
        System.out.println("Enter Amount to Deposit : ");
        amt = Nakshatra.nextLong();
        balance = balance + amt;
    }

    void withdrawal() {
        long amt;
        System.out.println("Enter Amount to withdraw : ");
        amt = Nakshatra.nextLong();
        if (balance >= amt) {
            balance = balance - amt;
        } else {
            System.out.println("Less Balance..Transaction Failed..");
        }
    }

    boolean search(String acn) {
        if (accno.equals(acn)) {
            showAccount();
            return (true);
        }
        return (false);
    }
    }
              public class Main{
       public static void main(String arg[]) {
        Scanner Nakshatra = new Scanner(System.in);

        System.out.print("Enter number of customers : ");
        int n = Nakshatra.nextInt();
        Bank C[] = new Bank[n];
        for (int i = 0; i < C.length; i++) {
            C[i] = new Bank();
            C[i].openAccount();
        }
        
        int ch;
        do {
            System.out.println("Main Menu\n1. Display\n2. Search By Account\n3. Deposit\n4. Withdrawal\n5.Exit ");
                System.out.println("Choose :"); 
                ch = Nakshatra.nextInt();
                switch (ch) {
                    case 1:
                        for (int i = 0; i < C.length; i++) {
                            C[i].showAccount();
                        }
                        break;

                    case 2:
                        System.out.print("Enter Account No U Want to Search...: ");
                        String acn = Nakshatra.next();
                        boolean found = false;
                        for (int i = 0; i < C.length; i++) {
                            found = C[i].search(acn);
                            if (found) {
                                break;
                            }
                        }
                        if (!found) {
                            System.out.println("Search Failed..Account Not Exist..");
                        }
                        break;

                    case 3:
                        System.out.print("Enter Account No : ");
                        acn = Nakshatra.next();
                        found = false;
                        for (int i = 0; i < C.length; i++) {
                            found = C[i].search(acn);
                            if (found) {
                                C[i].deposit();
                                break;
                            }
                        }
                        if (!found) {
                            System.out.println("No such account");
                        }
                        break;

                    case 4:
                        System.out.print("Enter Account No : ");
                        acn = Nakshatra.next();
                        found = false;
                        for (int i = 0; i < C.length; i++) {
                            found = C[i].search(acn);
                            if (found) {
                                C[i].withdrawal();
                                break;
                            }
                        }
                        if (!found) {
                            System.out.println("No such account");
                        }
                        break;

                    case 5:
                        System.out.println("Nakshatra's Bank CLosed!!!");
                        break;
                }
            }
            while (ch != 5);
        }
    }
