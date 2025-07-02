# norrmalcodesc-
1. Roman to Integer



using System;
using System.Collections.Generic;

public class Solution {

    public int RomanToInt(string s) {
     
        int ans = 0;
        Dictionary<char, int> roman = new Dictionary<char, int>();
        
        roman['I'] = 1;
        roman['V'] = 5;
        roman['X'] = 10;
        roman['L'] = 50;
        roman['C'] = 100;
        roman['D'] = 500;
        roman['M'] = 1000;

        for (int i = 0; i + 1 < s.Length; ++i) {
            if (roman[s[i]] < roman[s[i + 1]]) {
                ans -= roman[s[i]];
            } else {
                ans += roman[s[i]];
            }
        }

        return ans + roman[s[s.Length - 1]];
    }
}

public class Program
{
    
    public static void Main(string[] args)
    
    {
    
        Solution sol = new Solution();

        // Test cases
        string[] testCases = { "III", "IV", "IX", "LVIII", "MCMXCIV" };

        foreach (string roman in testCases)
        {
            int result = sol.RomanToInt(roman);
            Console.WriteLine($"Roman numeral {roman} = {result}");
        }
    }
}
