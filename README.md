package org.example;


import java.util.ArrayList;
import java.util.List;
import java.util.Objects;

public class PersonalAccount {

    private Integer accountNumber;
    private String accountHolder;
    private double balance;
    private final List<Amount> transactions = new ArrayList<>();


    public PersonalAccount(Integer accountNumber, String accountHolder) {
        this.accountNumber = accountNumber;
        this.accountHolder = accountHolder;
    }

    public Integer getAccountNumber() {
        return accountNumber;
    }

    public void setAccountNumber(Integer accountNumber) {
        this.accountNumber = accountNumber;
    }

    public String getAccountHolder() {
        return accountHolder;
    }

    public void setAccountHolder(String accountHolder) {
        this.accountHolder = accountHolder;
    }

    public double getBalance() {
        return balance;
    }

    public void setBalance(double balance) {
        this.balance = balance;
    }

    public List<Amount> getTransactions() {
        return transactions;
    }

    @Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (!(o instanceof PersonalAccount that)) return false;
        return Double.compare(getBalance(), that.getBalance()) == 0 && Objects.equals(getAccountNumber(), that.getAccountNumber()) && Objects.equals(getAccountHolder(), that.getAccountHolder()) && Objects.equals(getTransactions(), that.getTransactions());
    }

    @Override
    public int hashCode() {
        return Objects.hash(getAccountNumber(), getAccountHolder(), getBalance(), getTransactions());
    }

    @Override
    public String toString() {
        return "PersonalAccount{" +
                "accountNumber=" + accountNumber +
                ", accountHolder='" + accountHolder + '\'' +
                ", balance=" + balance +
                ", transactions=" + transactions +
                '}';
    }

    public void deposit(double amount) {
        balance += amount;
        transactions.add(new Amount(amount, "deposit"));
    }

    public void withdraw(double amount) {
        if (balance < amount) {
            System.out.println("Ты бомж");
        }
        balance -= balance;
        transactions.add(new Amount(amount, "withdraw"));
    }

    void printTransactionHistory() {
        for (Amount trans: transactions) {
            System.out.println(trans);
        }
    }


}
