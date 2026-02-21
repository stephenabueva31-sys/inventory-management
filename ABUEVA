using System;
using InventoryApp.Services;

namespace InventoryApp.Views
{
    public class InventoryView
    {
        private InventoryService _service = new InventoryService();

        public void Run()
        {
            bool running = true;

            while (running)
            {
                Console.WriteLine("\n--- Inventory Management System ---");
                Console.WriteLine("1. View Inventory");
                Console.WriteLine("2. Update Stock");
                Console.WriteLine("3. Reset Inventory");
                Console.WriteLine("4. Exit");
                Console.Write("Select an option: ");

                string choice = Console.ReadLine();

                switch (choice)
                {
                    case "1":
                        DisplayInventory();
                        break;

                    case "2":
                        UpdateStockFlow();
                        break;

                    case "3":
                        _service.ResetInventory();
                        Console.WriteLine("Inventory reset to initial values.");
                        break;

                    case "4":
                        running = false;
                        break;

                    default:
                        Console.WriteLine("Invalid option. Try again.");
                        break;
                }
            }
        }

        private void DisplayInventory()
        {
            string[,] data = _service.GetInventory();

            Console.WriteLine("\nProduct\t\tStock");
            Console.WriteLine("-----------------------");

            for (int i = 0; i < data.GetLength(1); i++)
            {
                Console.WriteLine($"{i + 1}. {data[0, i]}\t{data[1, i]}");
            }
        }

        private void UpdateStockFlow()
        {
            string[,] data = _service.GetInventory();
            DisplayInventory();

            Console.Write($"Enter product number (1-{data.GetLength(1)}): ");

            if (int.TryParse(Console.ReadLine(), out int index) &&
                index >= 1 && index <= data.GetLength(1))
            {
                Console.Write("Enter new quantity: ");

                if (int.TryParse(Console.ReadLine(), out int newQty) && newQty >= 0)
                {
                    _service.UpdateStock(index - 1, newQty.ToString());
                    Console.WriteLine("Stock updated successfully.");
                }
                else
                {
                    Console.WriteLine("Invalid quantity.");
                }
            }
            else
            {
                Console.WriteLine("Invalid product number.");
            }
        }
    }
}
