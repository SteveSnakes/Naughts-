# Naughts-
using System;

public class Program
{
    static string[] grid = { "1", "2", "3", "4", "5", "6", "7", "8", "9" };
    static bool player1Turn = true;
	static bool exitGame = true;
    static int box;

    public static void Main()
    {
         while (exitGame) // Clear the console before each iteration
        {
			Console.Clear();

            Console.WriteLine("Welcome to\n");
            Console.WriteLine("____________             ________                   ________           ");
            Console.WriteLine("___  __/__(_)______      ___  __/_____ _______      ___  __/__________ ");
            Console.WriteLine(@"__  /  __  /_  ___/________  /  _  __ `/  ___/________  /  _  __ \  _ \");
            Console.WriteLine("_  /   _  / / /__ _/_____/  /   / /_/ // /__ _/_____/  /   / /_/ /  __/");
            Console.WriteLine(@"/_/    /_/  \___/        /_/    \__,_/ \___/        /_/    \____/\___/ ");
            Console.WriteLine("\nMain Menu:");
            Console.WriteLine("1. Start Game");
            Console.WriteLine("2. Rules");
            Console.WriteLine("Enter your choice (1, or 2): ");
            string choice = Console.ReadLine();

            switch (choice)
            {
                case "1":
                    Console.Clear(); 
           			PlayerNames(); // function
		   			Console.WriteLine("\n");
          			PlayGame();	
                    break; // breaks out of the loop
                case "2":
					Console.Clear();
                    Console.WriteLine("WOW! There's actually someone who's this dumb...");
                    Console.WriteLine("\nWell, here you go:");
                    Console.WriteLine("1. Two players take turns marking a spot on a 3x3 square.");
                    Console.WriteLine("2. The player to first align three spots diagonally, horizontally or vertically wins!");
                    Console.WriteLine("3. If the square is filled, it's a boring tie :( ");
                    Console.WriteLine("\nPress Enter to return to the main menu.");
                    Console.ReadLine();
					break;
                default:
					Console.Clear();
                    Console.WriteLine("Invalid choice. Please enter 1, 2, or 3.");
                    Console.WriteLine("\nPress Enter to return to the main menu.");
                    Console.ReadLine();
                    break;
            }
		 }
	}
    static void PlayGame()
    {
        while (true)
        {
            DrawGrid();

            if (player1Turn)
                Console.WriteLine("{Player 1} Turn!");
            else
                Console.WriteLine("{Player 2} Turn!");

            box = int.Parse(Console.ReadLine()); // line input for players to play, expecting the user to enter a number.

            if (box >= 1 && box <= 9 && grid[box - 1] != "X" && grid[box - 1] != "O") // checks if the entered value is 1-9 and not already marked by "X" or "O"
            {
                int gridIndex = box - 1; // if conditions are met minus 1 to adjust to zero-based numbering to access grid elements 

                if (player1Turn)
                    grid[gridIndex] = "X";
                else
                    grid[gridIndex] = "O";

                player1Turn = !player1Turn;
            }
            else
            {
                Console.WriteLine("Warning: That box's already taken! Please try again.");
            }
        }
    }

    static void DrawGrid()
    {
        for (int i = 0; i < 3; i++) // iterates over the rows starting from 0-2
        {
            for (int j = 0; j < 3; j++) // iterates over the columns starting from 0-2
            {
                Console.Write(grid[i * 3 + j] + "|"); // Writes out the elements stored in the grid starting from the row or i value * 3 then moving down the column + j
            }

            Console.WriteLine(""); // This statment writes a blank line after j+l
            if (i < 2)
                Console.WriteLine("______");
        }
    }

    static void PlayerNames()
    {
        Console.WriteLine("Please enter the name of the first player: ");
        string player1 = Console.ReadLine();
        Console.WriteLine("Please enter the name of the second player: ");
        string player2 = Console.ReadLine();
        Console.WriteLine("\nHello, {player1} and {player2}! Let the game begin!");
    }
}
