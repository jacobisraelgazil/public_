import java.math.BigInteger;
import java.util.ArrayList;
import java.util.List;

public class PrimeGenerator {
    
    // Method to generate prime numbers within a given range
    public static List<BigInteger> generatePrimes(BigInteger start, BigInteger end) {
        List<BigInteger> primes = new ArrayList<>();
        BigInteger current = start;

        // Ensure starting point is greater than or equal to 2
        if (current.compareTo(BigInteger.TWO) < 0) {
            current = BigInteger.TWO;
        }

        // Find the first prime number greater than or equal to the start value
        current = current.isProbablePrime(100) ? current : current.nextProbablePrime();

        // Loop through the range to find all primes
        while (current.compareTo(end) <= 0) {
            primes.add(current);
            current = current.nextProbablePrime();
        }

        return primes;
    }

    // Main method to test the prime generation
    public static void main(String[] args) {
        // Define the range for prime generation
        BigInteger start = new BigInteger("10");
        BigInteger end = new BigInteger("100");

        // Generate primes within the specified range
        List<BigInteger> primes = generatePrimes(start, end);

        // Print the generated prime numbers
        System.out.println("Prime numbers between " + start + " and " + end + " are:");
        for (BigInteger prime : primes) {
            System.out.println(prime);
        }
    }
}
