# Desafio: Sistema de Gerenciamento de Estacionamento em C# + .NET

## Requisitos:

1. Classe "Estacionamento" com as variáveis:
   - `precoInicial`: Tipo decimal. Preço cobrado para deixar o veículo estacionado.
   - `precoPorHora`: Tipo decimal. Preço por hora que o veículo permanece estacionado.
   - `veiculos`: Lista de strings representando as placas dos veículos estacionados.

2. Métodos da classe:
   - **AdicionarVeiculo:** Armazena a placa do veículo na lista.
   - **RemoverVeiculo:** Verifica se o veículo está estacionado, solicita as horas e calcula o valor a ser pago.
   - **ListarVeiculos:** Mostra as placas dos veículos no estacionamento ou exibe "Não há veículos estacionados".

3. Menu interativo com as seguintes opções:
   - Cadastrar veículo
   - Remover veículo
   - Listar veículos
   - Encerrar

# Desafio Concluído no Bootcamp C# + .NET da DIO! 🚗💻🎓

Foi uma experiência enriquecedora participar do desenvolvimento de um sistema de gerenciamento de estacionamento em C# e .NET, guiado pelo conhecimento do [professor]. 🖥️ Na construção da classe "Estacionamento", destaco os métodos fundamentais:

1️⃣ **AdicionarVeiculo:** Responsável por armazenar a placa do veículo na lista.

2️⃣ **RemoverVeiculo:** Verifica se o veículo está estacionado, solicita as horas e calcula o valor a ser pago.

3️⃣ **ListarVeiculos:** Mostra todas as placas dos veículos presentes no estacionamento.

## 🚀 Tecnologias Utilizadas:

| Tecnologia | Versão  |
|------------|---------|
| C#         | 10.0    |
| .NET       | 6.0.1   |

## 📝 Implementei um menu interativo oferecendo as seguintes opções:

- Cadastrar veículo
- Remover veículo
- Listar veículos
- Encerrar

O código está pronto para uso, bem estruturado e de fácil compreensão.


## Solução:
```csharp
using System;
using System.Collections.Generic;

class Estacionamento
{
    private decimal precoInicial;
    private decimal precoPorHora;
    private List<string> veiculos;

    public Estacionamento(decimal precoInicial, decimal precoPorHora)
    {
        this.precoInicial = precoInicial;
        this.precoPorHora = precoPorHora;
        this.veiculos = new List<string>();
    }

    public void AdicionarVeiculo()
    {
        Console.WriteLine("Digite a placa do veículo:");
        string placa = Console.ReadLine();
        veiculos.Add(placa);
        Console.WriteLine("Veículo cadastrado com sucesso!");
    }

    public void RemoverVeiculo()
    {
        Console.WriteLine("Digite a placa do veículo a ser removido:");
        string placa = Console.ReadLine();

        if (veiculos.Contains(placa))
        {
            Console.WriteLine("Digite a quantidade de horas que o veículo permaneceu no estacionamento:");
            int horasEstacionado = int.Parse(Console.ReadLine());

            decimal valorCobrado = precoInicial + (horasEstacionado * precoPorHora);
            Console.WriteLine($"Valor a ser pago: {valorCobrado:C}");

            veiculos.Remove(placa);
            Console.WriteLine("Veículo removido com sucesso!");
        }
        else
        {
            Console.WriteLine("Veículo não encontrado no estacionamento.");
        }
    }

    public void ListarVeiculos()
    {
        if (veiculos.Count > 0)
        {
            Console.WriteLine("Veículos estacionados:");
            foreach (var veiculo in veiculos)
            {
                Console.WriteLine(veiculo);
            }
        }
        else
        {
            Console.WriteLine("Não há veículos estacionados.");
        }
    }
}

class Program
{
    static void Main()
    {
        Estacionamento estacionamento = new Estacionamento(5.0m, 2.0m);

        int opcao;
        do
        {
            Console.WriteLine("Menu:");
            Console.WriteLine("1. Cadastrar veículo");
            Console.WriteLine("2. Remover veículo");
            Console.WriteLine("3. Listar veículos");
            Console.WriteLine("4. Encerrar");
            Console.Write("Escolha uma opção: ");
            opcao = int.Parse(Console.ReadLine());

            switch (opcao)
            {
                case 1:
                    estacionamento.AdicionarVeiculo();
                    break;
                case 2:
                    estacionamento.RemoverVeiculo();
                    break;
                case 3:
                    estacionamento.ListarVeiculos();
                    break;
                case 4:
                    Console.WriteLine("Encerrando o programa. Obrigado!");
                    break;
                default:
                    Console.WriteLine("Opção inválida. Tente novamente.");
                    break;
            }
        } while (opcao != 4);
    }
}


