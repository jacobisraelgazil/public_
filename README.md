
// Method to generate prime numbers within a given range; it is the responsible for generating prime numbers in a specific range; This line initializes an "ArrayList" named "primes" to store the prime numbers that will be found within the specified range;"biginteger current= start" purpose is to iterate the numbers from "start" to "end".
public static List<BigInteger> generatePrimes(BigInteger start, BigInteger end) {
    List<BigInteger> primes = new ArrayList<>();
    BigInteger current = start;

    // Ensure the starting point is greater than or equal to 2; "if (current.compareTo(BigInteger.TWO) < 0) {" the purpose of this is to check if the value is less than 2, since 2 is the lowest prime number, any starting value that is lower than 2 is invalid.

    if (current.compareTo(BigInteger.TWO) < 0) {
        current = BigInteger.TWO;
    }

    // Find the first prime number greater than or equal to the start value; This ensures that the prime generation process starts with a prime number
    current = current.isProbablePrime(100) ? current : current.nextProbablePrime();

    // Loop through the range to find all primes;this is the core of the prime generation process. it systematically finds each subsequent prime numbers.
    while (current.compareTo(end) <= 0) {
        primes.add(current);
        current = current.nextProbablePrime();
    }

    return primes;
}

// Main method to test the prime generation.
public static void main(String[] args) {
    // Define the range for prime generation;"start" this define the starting of range up to which prime numbers will be generated; "end" this is the ending point of the prime numbers that will be generated.
    BigInteger start = new BigInteger("10");
    BigInteger end = new BigInteger("100");

    // Generate primes within the specified range
    List<BigInteger> primes = generatePrimes(start, end);

    // Print the generated prime numbers; it also provide context to the user and without this message, the user might not understand the list represents; "biginteger prime" is the core functionality for displaying the prime numbers that were generated.
    System.out.println("Prime numbers between " + start + " and " + end + " are:");
    for (BigInteger prime : primes) {
        System.out.println(prime);
    }
}
