using System;

class Program
{
    static void Main()
    {
        Console.Write("Введите количество чисел N: ");
        int N = int.Parse(Console.ReadLine());
        int[] numbers = new int[N];

        // Вводим массив чисел
        Console.WriteLine("Введите числа по одному в строке:");
        for (int i = 0; i < N; i++)
        {
            numbers[i] = int.Parse(Console.ReadLine());
        }

        int K = 0; // Счётчик чётных чисел

        Console.WriteLine("Чётные числа из набора:");
        for (int i = 0; i < N; i++)
        {
            if (numbers[i] % 2 == 0)
            {
                Console.Write(numbers[i] + " ");
                K++;
            }
        }

        Console.WriteLine(); // Перевод строки после вывода чисел
        Console.WriteLine("Количество чётных чисел: " + K);
    }
}
