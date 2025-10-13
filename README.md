using System;

class Program
{
    static void Main()
    {
        double R = Convert.ToDouble(Console.ReadLine());
        int N = Convert.ToInt32(Console.ReadLine());

        double[] a = new double[N];
        for (int i = 0; i < N; i++)
        {
            a[i] = Convert.ToDouble(Console.ReadLine());
        }

        int bI = 0;
        double bD = (a[0] + a[1]) - R;

        for (int i = 1; i < N - 1; i++)
        {
            double sum = a[i] + a[i + 1];
            double diff = sum - R;
            if (diff < bD)
            {
                bD = diff;
                bI = i;
            }
        }

        Console.WriteLine(a[bI] + " " + a[bI + 1]);
    }
}
