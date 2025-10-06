using System;

class Program
{
    // Функция проверки степени 5
    static bool IsPower5(int K)
    {
        if (K < 1)
            return false;
        while (K % 5 == 0)
        {
            K /= 5;
        }
        return K == 1;
    }

    static void Main()
    {
        int[] numbers = new int[10];
        int count = 0;

        Console.WriteLine("Введите 10 положительных целых чисел:");
        for (int i = 0; i < 10; i++)
        {
            numbers[i] = int.Parse(Console.ReadLine());
            if (IsPower5(numbers[i]))
                count++;
        }

        Console.WriteLine($"Количество степеней числа 5: {count}");
    }
}
