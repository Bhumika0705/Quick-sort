# Quick-sort
Quick sort in java
public class quicksort {
    public quicksort() {
    }

    static void displayArr(int[] arr) {
        int[] var1 = arr;
        int var2 = arr.length;

        for(int var3 = 0; var3 < var2; ++var3) {
            int val = var1[var3];
            System.out.println("" + val + " ");
        }

    }

    static void swap(int[] arr, int x, int y) {
        int temp = arr[x];
        arr[x] = arr[y];
        arr[y] = temp;
    }

    static int partition(int[] arr, int st, int end) {
        int pivot = arr[st];
        int cnt = 0;

        int pivotidx;
        for(pivotidx = st + 1; pivotidx <= end; ++pivotidx) {
            if (arr[pivotidx] <= pivot) {
                ++cnt;
            }
        }

        pivotidx = st + cnt;
        swap(arr, st, pivotidx);
        int i = st;
        int j = end;

        while(i < pivotidx && j > pivotidx) {
            while(arr[i] <= pivot) {
                ++i;
            }

            while(arr[j] >= pivot) {
                --j;
            }

            if (i < pivotidx && j > pivotidx) {
                swap(arr, i, j);
                ++i;
                --j;
            }
        }

        return pivotidx;
    }

    static void quickSort(int[] arr, int st, int end) {
        if (st < end) {
            int pi = partition(arr, st, end);
            quickSort(arr, st, pi - 1);
            quickSort(arr, pi + 1, end);
        }
    }

    public static void main(String[] args) {
        int[] arr = new int[]{6, 3, 1, 5, 4};
        System.out.println("Array before Sorting");
        displayArr(arr);
        System.out.println();
        quickSort(arr, 0, arr.length - 1);
        System.out.println("Array after Sorting");
        displayArr(arr);
    }
}
