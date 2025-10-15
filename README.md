using System;

class Program
{
    static void Main()
    {
        int[] A = { 5, 3, 7, 1, 4 }; 
        int n = A.Length;

        int[] I = new int[n];
        for (int i = 0; i < n; i++)
            I[i] = i + 1;

        for (int pass = 0; pass < n - 1; pass++)
        {
            for (int j = 0; j < n - 1 - pass; j++)
            {
                int left = I[j] - 1;
                int right = I[j + 1] - 1;
                if (A[left] > A[right])
                {
                    int t = I[j];
                    I[j] = I[j + 1];
                    I[j + 1] = t;
                }
            }
        }

        for (int i = 0; i < n; i++)
        {
            Console.Write(I[i]);
            if (i + 1 < n) Console.Write(" ");
        }
    }
}
