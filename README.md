import java.util.Scanner;

public class PermutationChecker {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int numTestCases = scanner.nextInt();
        scanner.nextLine();
        
        for (int i = 0; i < numTestCases; i++) {
            String pattern = scanner.nextLine();
            String text = scanner.nextLine();

            String result = checkPermutationExists(pattern, text);
            System.out.println(result);
        }
        	scanner.close();
    }

    public static String checkPermutationExists(String pattern, String text) {
        int[] patternFreq = new int[30];
        int[] textFreq = new int[30];

        for (char c : pattern.toCharArray()) {
            patternFreq[c - 'a']++;
        }

        for (int i = 0; i < text.length(); i++) {
                       textFreq[text.charAt(i) - 'a']++;
                       
            if (i >= pattern.length()) {
                textFreq[text.charAt(i - pattern.length()) - 'a']--;
            }

                if (arraysAreEqual(textFreq, patternFreq)) {
                return "Yes";
            }
        }

        return "No";
    }

    public static boolean arraysAreEqual(int[] arr1, int[] arr2) {
        if (arr1.length != arr2.length) {
            return false;
        }

        for (int i = 0; i < arr1.length; i++) {
            if (arr1[i] != arr2[i]) {
                return false;
            }
        }

        return true;
    }
}
