using System;
using System.Collections.Generic;

namespace ToDoList
{
    class Program
    {
        static List<string> tasks = new List<string>();

        static void Main(string[] args)
        {
            Console.WriteLine("Добро пожаловать в список дел!");

            while (true)
            {
                Console.WriteLine("\nВыберите действие:");
                Console.WriteLine("1. Добавить дело");
                Console.WriteLine("2. Вывести список дел");
                Console.WriteLine("3. Отметить дело как выполненное");
                Console.WriteLine("4. Удалить дело");
                Console.WriteLine("5. Выйти");

                string choice = Console.ReadLine();

                switch (choice)
                {
                    case "1":
                        AddTask();
                        break;
                    case "2":
                        ShowTasks();
                        break;
                    case "3":
                        MarkTaskCompleted();
                        break;
                    case "4":
                        RemoveTask();
                        break;
                    case "5":
                        Environment.Exit(0);
                        break;
                    default:
                        Console.WriteLine("Неверный выбор. Попробуйте снова.");
                        break;
                }
            }
        }

        static void AddTask()
        {
            Console.Write("Введите новое дело: ");
            string newTask = Console.ReadLine();
            tasks.Add(newTask);
            Console.WriteLine("Дело добавлено в список.");
        }

        static void ShowTasks()
        {
            if (tasks.Count == 0)
            {
                Console.WriteLine("Список дел пуст.");
            }
            else
            {
                Console.WriteLine("\nСписок дел:");
                for (int i = 0; i < tasks.Count; i++)
                {
                    Console.WriteLine($"{i + 1}. {tasks[i]}");
                }
            }
        }

        static void MarkTaskCompleted()
        {
            ShowTasks();

            if (tasks.Count > 0)
            {
                Console.Write("Введите номер дела, которое вы хотите отметить как выполненное: ");
                if (int.TryParse(Console.ReadLine(), out int taskIndex))
                {
                    if (taskIndex > 0 && taskIndex <= tasks.Count)
                    {
                        tasks[taskIndex - 1] = "✅ " + tasks[taskIndex - 1];
                        Console.WriteLine("Дело отмечено как выполненное.");
                    }
                    else
                    {
                        Console.WriteLine("Неверный номер дела.");
                    }
                }
                else
                {
                    Console.WriteLine("Неверный ввод.");
                }
            }
        }

        static void RemoveTask()
        {
            ShowTasks();

            if (tasks.Count > 0)
            {
                Console.Write("Введите номер дела, которое вы хотите удалить: ");
                if (int.TryParse(Console.ReadLine(), out int taskIndex))
                {
                    if (taskIndex > 0 && taskIndex <= tasks.Count)
                    {
                        tasks.RemoveAt(taskIndex - 1);
                        Console.WriteLine("Дело удалено из списка.");
                    }
                    else
                    {
                        Console.WriteLine("Неверный номер дела.");
                    }
                }
                else
                {
                    Console.WriteLine("Неверный ввод.");
                }
            }
        }
    }
}
