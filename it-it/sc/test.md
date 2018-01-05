# Unit Test di uno Smart Contract

Dopo aver letto il documento precedente, siamo stati in grado di utilizzare C # in Visual Studio 2015 per preparare uno smart contract. Come possiamo fare unit test dopo aver scritto un contratto intelligente?

## Scrivere unit tests

Per esempio, si crea il seguente contratto intelligente, che contiene tre parametri, il valore restituito è int.


```c#
using Neo.SmartContract.Framework;
using Neo.SmartContract.Framework.Services.Neo;

namespace Neo.SmartContract
{
    public class Test1: SmartContract
    {
        public static int Main (int a, int b, int c)
        {
            if (a> b)
                return a * sum (b, c);
            else
                return sum (a, b) * c;
        }

        public static int sum (int a, int b)
        {
            return a + b;
        }
    }
}
```

Dopo la compilazione, genera il file `Test1.avm` del contratto. Possiamo creare un progetto unit test e testare `Test1.avm`.

Fper prima cosa crea un'app Console in C# (.Net Framework) con Visual Studio, con .NET Framework 4.6.2 o successivi. Poi aggiungere una referenza a `Neo.dll` e `neon.dll`.

> [!Nota]
> Questi due file possono essere ottenuti compilando [Neo](https://github.com/neo-project/neo) e [neo-vm](https://github.com/neo-project/neo-vm).

> Ain alternativa, puoi semplicemente aggiungere i pacchetti NuGet "NEO" e "Neo.VM" al tuo progetto. Puoi farlo facendo clic con il tasto destro del mouse sul progetto del contratto sul Solution Explorer, vai a Browse, cerca NEO e installa i pacchetti richiesti.

```c#
using System;
using System.IO;
using System.Linq;
using Neo;
using Neo.VM;
using Neo.Cryptography;

namespace ConsoleApplication1
{
    class program
    {
        static void Main(string[] args)
        {
            var engine = new ExecutionEngine(null, Crypto.Default);
            engine.LoadScript(File.ReadAllBytes(@ "C: \ ... \ Test1.avm"));

            using (ScriptBuilder sb = new ScriptBuilder())
            {
                sb.EmitPush(2); // corresponds to the parameter c
                sb.EmitPush(4); // corresponds to the parameter b
                sb.EmitPush(3); // corresponds to the parameter a
                engine.LoadScript(sb.ToArray());
            }

            engine.Execute(); // start execution

            var result = engine.EvaluationStack.Peek().GetBigInteger(); // set the return value here
            Console.WriteLine($"Execution result {result}");
            Console.ReadLine();
        }
    }
}
```

Compilazione dell'output: risultato dell'esecuzione 14, come previsto

Nota: Se usi il codice sopra per passare i parametri, fai attenzione alla parte superiore della pila corrispondente al primo parametro, per comodità puoi anche passare i parametri con il seguente codice.

```c#
using (ScriptBuilder sb = new ScriptBuilder())
{
    int[] parameter = {3, 4, 2};
    parameter.Reverse().ToList().ForEach(p => sb.EmitPush(p));
    engine.LoadScript(sb.ToArray());
}
```
Se il valore restituito del contratto intelligente non è di tipo int, ma è bool o altro tipo, è necessario impostare `engine.EvaluationStack.Peek (). GetBigInteger ()` agli altri valori, come mostrato in figura

[](/assets/test_1.jpg)

------

### 📖 Il documento è in corso di modifica

Il documento è in fase di modifica e lo completeremo il prima possibile. È possibile visualizzare altri documenti su [Github wiki](https://github.com/neo-project/neo/wiki)o vieni al nostro [sito web NEO ufficiale](http://www.neo.org) e guardati intorno.

NEO è un progetto open source, se sei interessato, puoi anche contribuire ai documenti per sviluppatori creando Pull request su GitHub, i documenti per il progetto possono essere trovati su [github.com/neo-project/docs](https://github.com/neo-project/docs), Grazie per il tuo contributo.
