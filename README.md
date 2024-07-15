# exercises-page-3
package exercises;

import java.util.Scanner;

public class exercises3 {
    // q1
    public static float q1a(int length, int[] array) {
        float count = 0, sum = 0, avg;
        for(int i=1; i<length; i++){
            if (array[i] < array[0]){
                count++;
                sum += array[i];
            }
        }
        avg = sum / count;
        return avg;
    }
    public static float q1b(int length, int[] array) {
        float count = 0, sum = 0, avg;
        for(int i=0; i<length - 1; i++){
            if (array[i] < array[length -1]){
                count++;
                sum += array[i];
            }
        }
        avg = sum / count;
        return avg;
    }
    //q2
    public static void count_digits() {
        Scanner in = new Scanner(System.in);

        int[] arr = new int[10];
        int num = in.nextInt();

        while (num > 0)
        {
            arr[num % 10]++;
            num /= 10;
        }
        for (int i = 1; i < 10; i++) {
            if (arr[i] > 0) {
                System.out.println("the digit " + i + " is found " + arr[i]);
            }
        }
    }
    //q3
    public static int find_missing(int[] a, int n) {
        int sum = (n * (n + 1)) / 2;

        int arrSum = 0;
        for (int i = 0; i < n - 1; i++) {
            arrSum += a[i];
        }

        return sum - arrSum;
    }
    static void q3() {
        int[] arr = {3,1,4};
        int missingNumber = find_missing(arr, 4);
        System.out.println("the missing number is: " + missingNumber);
    }
    //q4
    public static void numberSeries() {
        Scanner in = new Scanner(System.in);

        int[] arr = new int[12];
        int[] sequencesCount = new int[12];
        int currentLength = 0;

        for (int i = 0; i < 12; i++) {
            int num = in.nextInt();
            arr[i] = num;
        }

        for (int i = 0; i < 12; i++) {
            if (arr[i] == 1) {
                currentLength++;
                if (i == 11) {
                    sequencesCount[currentLength]++;
                }
            }
            else{
                if (currentLength > 0) {
                    sequencesCount[currentLength]++;

                }
                currentLength = 0;
            }
        }

        for (int i = 0; i < 12; i++) {
            if (sequencesCount[i] > 0) {
                System.out.println(sequencesCount[i] + " sequences of " + i + " digits");
            }
        }
    }
    //q5
    public static int midMax(float a, float b, float c) {
        if (b > a && b > c) {
            return 1;
        }
        else {
            return 0;
        }
    }
    public static int countPeaks(int[] heights, int size) {
        int count = 0;
        for (int i = 1; i < size - 1; i++) {
            if (midMax(heights[i - 1], heights[i], heights[i + 1]) == 1) {
                count++;
            }
        }
        return count;
    }
    //q6
    public static int arithmeticMean(int[] a, int n){
        int sum = 0;
        for(int i=0; i<n; i++){
            sum += a[i];
        }
        return sum / n;
    }
    public static double geometricMean(int[] a, int n){
        double sum = 1;
        for(int i=0; i<n; i++){
            sum *= a[i];
        }
        return Math.pow(sum, 1.0 / n);
    }
    public static double harmonicMean(int[] a, int n){
        double sum = 0;
        for(int i=0; i<n; i++){
            sum += (1.0 / a[i]);
        }
        return n / sum;
    }
    public static void meansInequality(){
        int[] arr = {2,4,6,8};
        int size = arr.length;
        System.out.println("result of harmonicMean is: " + arithmeticMean(arr, size));
        System.out.println("result of geometricMean is: " + geometricMean(arr, size));
        System.out.println("result of harmonicMean is: " + harmonicMean(arr, size));
    }
    //q8
    public static void printMatrix(int[][] matrix) {
        for (int[] row : matrix) {
            for (int value : row) {
                System.out.print(value + " ");
            }
            System.out.println();
        }
    }
    public static void MatrixSumNeighbors(){
        int[][] originalMatrix = {
                {1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}
            };
        int size = 3;
        int[][] newMatrix = new int[size][size];
        for (int row = 0; row < size; row++) {
            for (int col = 0; col < size; col++) {
                int sum = 0;
                for (int di = -1; di <= 1; di++) {
                    for (int dj = -1; dj <= 1; dj++) {
                        if (row + di >= 0 && row + di < size && col + dj >= 0 && col + dj < size) {
                            sum += originalMatrix[row + di][col + dj];
                        }
                    }
                }
                newMatrix[row][col] = sum;
            }
        }
        printMatrix(newMatrix);
    }
    //q9
    /*int[][] matrixA = {
                {1, 2, 3},
                {4, 5, 6},
                {7, 8, 9}
            };
            int[][] matrixB = {
                {1, 4, 7},
                {2, 5, 8},
                {3, 6, 9},
            };
            int size = 3;

            findMatchingRowsAndColumns(matrixA, matrixB, size);*/
    public static void findMatchingRowsAndColumns(int[][] matrixA, int[][] matrixB, int size) {
        int[][] newMatrix = new int[size][size];
        for (int row = 0; row < size; row++) {
            for (int col = 0; col < size; col++) {
                newMatrix[row][col] = matrixB[col][row];
            }
        }

        for (int row = 0; row < size; row++) {
            boolean match = true;
            for (int col = 0; col < size; col++) {
                if (matrixA[row][col] != newMatrix[row][col]) {
                    match = false;
                    break;
                }
            }
            if (match) {
                System.out.println("The row number " + (row + 1) + " is matching");
            }
        }
    }
    //q10
    public static void rightTurn() {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        int size = 3;
        int[][] newMatrix = new int[size][size];
        for (int row = 0; row < size; row++) {
            for (int col = 0; col < size; col++) {
                newMatrix[row][col] = matrix[size - col - 1][row];
            }
        }
        printMatrix(newMatrix);
    }
    //q11
    public static void q11() {
        int[][] matrix = {
            {4, 7, 1, 2},
            { 2,3,5,7 },
            { 8,2,5,1 },
            { 3,6,5,6 }
        };
        int size = 4;

        for (int i = 0; i < size; i++) {
            int min = matrix[i][0];
            int indexMin = 0;
            for (int j = 1; j < size; j++) {
                if (matrix[i][j] < min) {
                    min = matrix[i][j];
                    indexMin = j;
                }
            }
            int temp = matrix[i][i];
            matrix[i][i] = min;
            matrix[i][indexMin] = temp;
        }
        for (int i = 0; i < size; i++) {
            for (int j = 0; j < size; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }
    //q13
    public static int countRectangles(int[][] picture){
        int count = 0;
        for (int i = 1; i < picture.length; i++){
            for (int j = 1; j < picture[0].length; j++){
                if (picture[i][j] == 1){
                    if (picture[i][j - 1] == 0 && picture[i - 1][j] == 0){
                        count++;
                    }
                }
            }
        }
        return count;
    }
    //q14
    /*int[] a = {206, 0, 300, 0, 406};
        System.out.println(removeZeros(a, 5));
        for (int i = 0; i < 5; i++)
        {
            System.out.println(a[i]);
        }*/
    public static int removeZeros(int[] a, int n) {
        int count = n;
        for (int i = 0; i < n; i++)
        {
            if (a[i] == 0) {
                count--;
                for (int j = i; j < n - 1; j++)
                {
                    a[j] = a[j + 1];
                }
            }
        }
        return count;
    }

    public static void main(String[] args) {
    }
}
