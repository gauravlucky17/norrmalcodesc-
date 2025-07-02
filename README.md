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


2.  Longest Common Prefix


using System;
using System.Collections.Generic;

public class Solution {
    public string LongestCommonPrefix(List<string> strs) {
        if (strs.Count == 0)
            return "";

        for (int i = 0; i < strs[0].Length; ++i) {
            for (int j = 1; j < strs.Count; ++j) {
                if (i == strs[j].Length || strs[j][i] != strs[0][i])
                    return strs[0].Substring(0, i);
            }
        }

        return strs[0];
    }
}

public class Program
{
    public static void Main(string[] args)
    {
        Solution sol = new Solution();

        // Test cases
        List<List<string>> testCases = new List<List<string>>
        {
            new List<string> { "flower", "flow", "flight" },
            new List<string> { "dog", "racecar", "car" },
            new List<string> { "interspecies", "interstellar", "interstate" },
            new List<string> { "throne", "throne" },
            new List<string> { "throne", "dungeon" },
            new List<string> { "" },
            new List<string> { }
        };

        foreach (var strs in testCases)
        {
            string prefix = sol.LongestCommonPrefix(strs);
            Console.WriteLine($"Input: [{string.Join(", ", strs)}]");
            Console.WriteLine($"Longest Common Prefix: \"{prefix}\"");
            Console.WriteLine();
        }
    }
}

