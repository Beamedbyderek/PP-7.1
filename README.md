# PP-7.1

package pp.pkg7.pkg1;


import java.text.NumberFormat;

public class Account {

    private final double RATE = 0.035;  // interest rate of 3.5%

    private long acctNumber;
    private double balance;
    private String name;
    //-----------------------------------------------------------------
    //  Sets up the account by defining its owner, account number,
    //  and initial balance.
    //-----------------------------------------------------------------

    public Account(String owner, long account, double initial) {
        name = owner;
        acctNumber = account;
        balance = initial;
    }
    
    public Account(String owner, long account) {
        name = owner;
        acctNumber = account;
        balance = 0;
    }
    //-----------------------------------------------------------------
    //  Deposits the specified amount into the account. Returns the
    //  new balance.
    //-----------------------------------------------------------------

    public double deposit(double amount) {
        balance = balance + amount;
        return balance;
    }

    //-----------------------------------------------------------------
    //  Withdraws the specified amount from the account and applies
    //  the fee. Returns the new balance.
    //-----------------------------------------------------------------
    public double withdraw(double amount, double fee) {
        balance = balance - amount - fee;
        return balance;
    }

    //-----------------------------------------------------------------
    //  Adds interest to the account and returns the new balance.
    //-----------------------------------------------------------------
    public double addInterest() {
        balance += (balance * RATE);
        return balance;
    }
    //-----------------------------------------------------------------
    //  Returns the current balance of the account.
    //-----------------------------------------------------------------

    public double getBalance() {
        return balance;
    }

    //-----------------------------------------------------------------
    //  Returns a one-line description of the account as a string.
    //-----------------------------------------------------------------
    public String toString() {
        NumberFormat fmt = NumberFormat.getCurrencyInstance();
        return (acctNumber + "\t" + name + "\t" + fmt.format(balance));
        
    }
    
}




////////////////////////////////////////////////New class//////////////////////////////////////////
\


package pp.pkg7.pkg1;

//********************************************************************
//  Transactions.java       
//
//  Demonstrates the creation and use of multiple Account objects.
//********************************************************************

public class Transactions
{
   //-----------------------------------------------------------------
   //  Creates some bank accounts and requests various services.
   //-----------------------------------------------------------------
   public static void main(String[] args)
   {
      Account acct1 = new Account("Ted Murphy", 72354, 102.56);
      Account acct2 = new Account("Jane Smith", 69713, 40.00);
      Account acct3 = new Account("Edward Demsey", 93757, 759.32);
      Account acct4 = new Account("john Doe", 20942);

      acct1.deposit(25.85);

      double smithBalance = acct2.deposit(500.00);
      System.out.println("Smith balance after deposit: " +
                          smithBalance);

      System.out.println("Smith balance after withdrawal: " + 
                          acct2.withdraw (430.75, 1.50));

      acct1.addInterest();
      acct2.addInterest();
      acct3.addInterest();

      System.out.println();
      System.out.println(acct1);
      System.out.println(acct2);
      System.out.println(acct3);
      System.out.println(acct4);
   }
}

