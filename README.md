# hlulani-hope-mashaba
standalone command line application
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace Recipe
{
    internal class Program
    {
        static void Main(string[] args)
        {
            // Recipe details for standalone application
            Console.WriteLine("Enter the Recipe Details");
            Recipe recipe = new Recipe();

            // Number of ingredients
            Console.WriteLine("Enter the number of ingredients: ");
            int numIngredients = int.Parse(Console.ReadLine());

            for (int i = 0; i < numIngredients; i++)
            {
                Ingredient ingredient = new Ingredient();
                Console.WriteLine($"\nEnter details for ingredient#{i + 1}:");

                Console.Write("Name of ingredient: ");
                ingredient.Name = Console.ReadLine();

                Console.Write("Quantity: ");
                ingredient.Quantity = double.Parse(Console.ReadLine());

                Console.Write("Unit of measurement: ");
                ingredient.Unit = Console.ReadLine();

                recipe.Ingredients.Add(ingredient);
            }

            // Number of steps
            Console.Write("\nEnter the number of steps: ");
            int numSteps = int.Parse(Console.ReadLine());

            for (int i = 0; i < numSteps; i++)
            {
                Step step = new Step();
                Console.WriteLine($"\nEnter the details for step #{i + 1}:");

                Console.Write("Description of the step: ");
                step.Description = Console.ReadLine();

                recipe.Steps.Add(step);
            }

            // Optional: Display Recipe
            recipe.DisplayRecipe();
        }

        // Ingredient class
        public class Ingredient
        {
            public string Name { get; set; }
            public double Quantity { get; set; }
            public string Unit { get; set; }  // Fixed typo: "String" to "string"
        }

        // Step class
        public class Step
        {
            public string Description { get; set; }
        }

        // Recipe class
        public class Recipe
        {
            public List<Ingredient> Ingredients { get; set; } = new List<Ingredient>();
            public List<Step> Steps { get; set; } = new List<Step>();

            public void DisplayRecipe()
            {
                // Display recipe steps
                Console.WriteLine("\nSteps:");
                for (int i = 0; i < Steps.Count; i++)
                {
                    Console.WriteLine($"{i + 1}. {Steps[i].Description}");  // Fixed index and logic error
                }
            }
        }
    }
}
