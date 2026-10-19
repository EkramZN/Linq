# Linq
Assignment 
up to code : 

using System;
using System.Linq;
using System.Collections.Generic;

class Program
{
    static void Main()
    {
        var result1 = ProductList.Where(p => p.Category == "Seafood");
        foreach (var p in result1)
        {
            Console.WriteLine(p.ProductName + p.UnitPrice);
        }

        var result2 = ProductList.Select(p => p.Name);
        foreach (var name in result2)
        {
            Console.WriteLine(name);
        }

        var result3 = ProductList.OrderBy(p => p.UnitPrice);
        foreach (var p in result3)
        {
            Console.WriteLine(p.ProductName + " " + p.UnitPrice);
        }

        var result4 = ProductList.Where(p => p.UnitPrice >= 10 && p.UnitPrice <= 30);

        var result5 = ProductList.Where(p => p.UnitsInStock > 0 && p.Category == "Condiments");

        var result6 = ProductList.Select(p => new { Name = p.ProductName, Price = p.UnitPrice, StockStatus = p.UnitsInStock > 0 ? "Available" : "Out of Stock" });
        foreach (var x in result6)
        {
            Console.WriteLine(x.Name);
        }

        var result7 = ProductList.Select((p, index) => new { p.ProductName, Index = index });
        foreach (var x in result7)
        {
            Console.WriteLine(x.Index + ". " + x.ProductName);
        }

        var result8 = ProductList.OrderBy(p => p.Category).ThenByDescending(p => p.UnitPrice);

        var result9 = ProductList.Where(p => p.Category == "Beverages").OrderByDescending(p => p.UnitsInStock);
        foreach (var p in result9)
        {
            Console.WriteLine(p.ProductName + p.UnitsInStock);
        }

        var result10 = from o in OrderList
                       where o.OrderDate.Year >= 1997
                       select new { o.CustomerID, o.OrderDate };

        var result11 = ProductList.Select((p, i) => i + " " + p.ProductName);

        string[] Arr = { "aPPLE", "AbAcUs", "bRaNcH", "BIUeBeRrY", "ClOvEr", "cHeRry" };
        var result12 = Arr.OrderBy(w => w.Length).ThenBy(w => w, StringComparer.OrdinalIgnoreCase);

        string[] digits = { "zero", "one", "two", "three", "four", "five", "six", "seven", "eight", "nine" };
        var result13 = digits.Where(d => d[1] == 'i').Reverse();
    }
}

