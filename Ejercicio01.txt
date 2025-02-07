using System;
using System.Threading;

namespace Tema2
{
    internal class Ejercicio01
    {
        static volatile int producto;
        static volatile Random random = new Random();

        static volatile bool continuar = false;
        static void Productor()
        {
            producto = random.Next(10);
            continuar = true;
        }
        static void Consumidor()
        {
            while (!continuar) { }
            Console.WriteLine("Consumidor: " + producto.ToString());
        }
        static void Main(string[] cosas)
        {
            Thread productor = new Thread(Productor);
            Thread consumidor = new Thread(Consumidor);
            productor.Start();
            consumidor.Start();
        }
    }
}
