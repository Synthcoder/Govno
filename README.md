using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.IO;

namespace _34
{
    internal class Program
    {
        static void Main()
        {
            string file = "1.txt";
            File.WriteAllLines(file,
                File.ReadAllLines(file).Where(s => int.Parse(s) >= 0));
        }
    }
}
