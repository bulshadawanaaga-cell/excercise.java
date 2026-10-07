import java.util.Date;

public class Loan {
    private double annualInterestRate;
    private int numberOfYears;
    private double loanAmount;
    private Date loanDate;

    // Default constructor
    public Loan() {
        this(2.5, 1, 1000);
    }

    // Constructor with specified parameters
    public Loan(double annualInterestRate, int numberOfYears, double loanAmount) {
        this.annualInterestRate = annualInterestRate;
        this.numberOfYears = numberOfYears;
        this.loanAmount = loanAmount;
        this.loanDate = new Date();
    }

    // Getter for annual interest rate
    public double getAnnualInterestRate() {
        return annualInterestRate;
    }

    // Setter for annual interest rate
    public void setAnnualInterestRate(double annualInterestRate) {
        this.annualInterestRate = annualInterestRate;
    }

    // Getter for number of years
    public int getNumberOfYears() {
        return numberOfYears;
    }

    // Setter for number of years
    public void setNumberOfYears(int numberOfYears) {
        this.numberOfYears = numberOfYears;
    }

    // Getter for loan amount
    public double getLoanAmount() {
        return loanAmount;
    }

    // Setter for loan amount
    public void setLoanAmount(double loanAmount) {
        this.loanAmount = loanAmount;
    }

    // Getter for loan date
    public Date getLoanDate() {
        return loanDate;
    }

    // Calculate monthly payment
    public double getMonthlyPayment() {
        double monthlyInterestRate = annualInterestRate / 1200;

        double monthlyPayment = (loanAmount * monthlyInterestRate)
                / (1 - (1 / Math.pow(
                        1 + monthlyInterestRate,
                        numberOfYears * 12
                )));

        return monthlyPayment;
    }

    // Calculate total payment
    public double getTotalPayment() {
        return getMonthlyPayment() * numberOfYears * 12;
    }
}
