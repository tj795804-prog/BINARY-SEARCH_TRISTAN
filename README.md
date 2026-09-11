/* Description: Performs a recursive binary search on a user-provided array.
   The user enters the number of elements, the elements themselves, and the
   target value. The array is sorted ascending before the search runs, and
   each recursive call prints the current low, high, and mid values so the
   shrinking search interval can be traced. The program prints the index of
   the target if found, or -1 if not found.

   Programmed by: <TRISTAN JOSHUA MAMALUMPONG <BSIT> <DATA STRUCTURES AND ALGORITHM>
   Last Modified: <SEPT 4, 2026>
   Version: 1.0
   Acknowledgements: <I used Claude.ai as a tool to support my work, ideas, research, and other tasks.
*/

import java.util.Arrays;
import java.util.Scanner;

public class Binary_Search {

    public static int bSearch(int[] arr, int target, int low, int high) {
        if (low > high) {
            return -1;
        }
        int mid = low + (high - low) / 2;
        if (arr[mid] == target) {
            return mid;
        }
        if (target < arr[mid]) {
            return bSearch(arr, target, low, mid - 1);
        }
        return bSearch(arr, target, mid + 1, high);
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter the number of elements in the array: ");
        int n = sc.nextInt();

        int[] numbers = new int[n];

        System.out.println("Enter " + n + " elements of the array:");
        for (int i = 0; i < n; i++) {
            System.out.print("Element [" + i + "]: ");
            numbers[i] = sc.nextInt();
        }

        Arrays.sort(numbers);
        System.out.println("Sorted array: " + Arrays.toString(numbers));

        System.out.print("Enter the target value to search for: ");
        int target = sc.nextInt();

        int result = bSearch(
                numbers,
                target,
                0,
                numbers.length - 1
        );

        if (result == -1) {
            System.out.println("Element not found.");
            System.out.println(-1);
        } else {
            System.out.println("Element found at index: " + result);
        }

        sc.close(); 
    }
}
