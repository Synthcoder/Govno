using System;

class Program
{
    // Процедура добавления цифры справа
    static void AddRightDigit(int D, ref int K)
    {
        K = K * 10 + D;
    }

    static void Main()
    {
        int K = 123;    // Исходное число
        int D1 = 4;     // Первая добавляемая цифра
        int D2 = 7;     // Вторая добавляемая цифра

        // Добавляем первую цифру и выводим результат
        AddRightDigit(D1, ref K);
        Console.WriteLine($"После добавления {D1}: {K}");

        // Добавляем вторую цифру и выводим результат
        AddRightDigit(D2, ref K);
        Console.WriteLine($"После добавления {D2}: {K}");
    }
}
