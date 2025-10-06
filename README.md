using System;

class Program
{
    // Функция для вычисления A^B, возвращает 0 если A <= 0
    static double Power1(double A, double B)
    {
        if (A <= 0)
            return 0;
        return Math.Exp(B * Math.Log(A));
    }

    static void Main()
    {
        // Ввод исходных данных
        Console.WriteLine("Введите значения A, B, C и P через пробел:");
        string[] input = Console.ReadLine().Split();
        double A = double.Parse(input[0]);
        double B = double.Parse(input[1]);
        double C = double.Parse(input[2]);
        double P = double.Parse(input[3]);

        // Вычисления
        double AP = Power1(A, P);
        double BP = Power1(B, P);
        double CP = Power1(C, P);

        // Вывод результатов
        Console.WriteLine($"A^P = {AP}");
        Console.WriteLine($"B^P = {BP}");
        Console.WriteLine($"C^P = {CP}");
    }
}
