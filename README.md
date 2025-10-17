using System;
using System.Collections.Generic;

int[] a = { 1, 1, 2, 3, 3, 3, 4, 4, 5 };
int K = 2;

if (a.Length > 0 && K > 0)
{

    var values = new List<int>();
    var lengths = new List<int>();

    for (int i = 0; i < a.Length; )
    {
        int v = a[i];
        int j = i + 1;
        while (j < a.Length && a[j] == v) j++;
        values.Add(v);
        lengths.Add(j - i);
        i = j;
    }

    if (K <= values.Count)
    {
        int k = K - 1;
        int last = values.Count - 1;

        
        int tmpV = values[k]; values[k] = values[last]; values[last] = tmpV;
        int tmpL = lengths[k]; lengths[k] = lengths[last]; lengths[last] = tmpL;
        int idx = 0;
        for (int r = 0; r < values.Count; r++)
            for (int c = 0; c < lengths[r]; c++)
                a[idx++] = values[r];
    }
}

Console.WriteLine(string.Join(", ", a));
Console.ReadKey();
