# SOLITARIO
CODIGO EN C#

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace MATRIZ
{
    internal class Program
    {
         static Random rnd = new Random();

         static void Main(string[] args)
         {
            int c = rnd.Next(6, 16);
            int f = rnd.Next(6, 16);
            char[,] ma = new char[c, f];
            for (int j = 0; j < c; j++)
            {
                for (int k = 0; k < f; k++)
                {
                    ma[j, k] = Convert.ToChar(rnd.Next(65, 91));
                    Console.Write(ma[j, k] + " ");
                }
                Console.WriteLine();
            }
            Console.WriteLine("INGRESE UNA FRASE");
            string z = Console.ReadLine();
            int conth = 0;
            int contv = 0;

            for (int x = 0; x < c; x++)
            {
                for (int y = 0; y < f; y++)
                {
                    if (ma[x, y] == z[0])
                    {
                        int tempCont = 0;
                        for (int i = 0; i < z.Length; i++)
                        {
                            if (y + i < f && ma[x, y + i] == z[i])
                            {
                                tempCont++;
                            }
                            else
                            {
                                break;
                            }
                        }
                        if (tempCont == z.Length)
                        {
                            Console.WriteLine("LA FRASE ES ENCONTRADA EN [{0},{1}]", x+1, y+1);
                            conth++;
                        }
                    }

                    
                    if (ma[x, y] == z[0])
                    {
                        int tempCont = 0;
                        for (int i = 0; i < z.Length; i++)
                        {
                            if (x + i < c && ma[x + i, y] == z[i])
                            {
                                tempCont++;
                            }
                            else
                            {
                                break;
                            }
                        }
                        if (tempCont == z.Length)
                        {
                            Console.WriteLine("LA FRASE ES ENCONTRADA EN [{0},{1}]" ,x+1,y+1);
                            contv++;
                        }
                    }
                }
            }

            Console.WriteLine($"La frase ha sido encontrada {0} veces horizontalmente y {1} veces verticalmente." ,conth,contv);
            Console.ReadKey();

        }
    }
}
