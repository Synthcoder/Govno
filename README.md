using System;
using System.IO;

class Program
{
    static void Main()
    {
        string file1 = Console.ReadLine();
        string file2 = Console.ReadLine();

        bool e1 = File.Exists(file1);
        bool e2 = File.Exists(file2);

        if (e1 && !e2)
        {
            var lines = File.ReadAllLines(file1);
            if (lines.Length == 0) { Console.WriteLine("Существующий файл пуст."); return; }
            File.WriteAllLines(file2, new string[] { lines[lines.Length - 1], lines[0] });
            Console.WriteLine("Готово. Создан файл: " + file2);
        }
        else if (!e1 && e2)
        {
            var lines = File.ReadAllLines(file2);
            if (lines.Length == 0) { Console.WriteLine("Существующий файл пуст."); return; }
            File.WriteAllLines(file1, new string[] { lines[lines.Length - 1], lines[0] });
            Console.WriteLine("Готово. Создан файл: " + file1);
        }
        else
        {
            Console.WriteLine("Ожидалось, что ровно один файл существует, а второй отсутствует.");
        }
    }
}
