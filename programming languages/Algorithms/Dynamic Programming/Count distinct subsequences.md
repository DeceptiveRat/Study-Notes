# 1. Definition
Given a string, find the count of distinct subsequences of it

# 2. Code
## (1) Dynamic programming

```cpp
// C++ program to count number of distinct
// subsequences of a given string.
#include <bits/stdc++.h>
using namespace std;
const int MAX_CHAR = 256;

// Returns count of distinct subsequences of str.
int countSub(string str)
{
    // Create an array to store index
    // of last
    vector<int> last(MAX_CHAR, -1);

    // Length of input string
    int n = str.length();

    // dp[i] is going to store count of distinct
    // subsequences of length i.
    int dp[n + 1];

    // Empty substring has only one subsequence
    dp[0] = 1;

    // Traverse through all lengths from 1 to n.
    for (int i = 1; i <= n; i++) {
        // Number of subsequences with substring
        // str[0..i-1]
        dp[i] = 2 * dp[i - 1];

        // If current character has appeared
        // before, then remove all subsequences
        // ending with previous occurrence.
        if (last[str[i - 1]] != -1)
            dp[i] = dp[i] - dp[last[str[i - 1]]];

        // Mark occurrence of current character
        last[str[i - 1]] = (i - 1);
    }

    return dp[n];
}

// Driver code
int main()
{
    cout << countSub("gfg");
    return 0;
}
```

Explanation:
If there are no repetitions, then count becomes double of count for n-1 because we get count(n-1) more subsequences by adding the current character to the end of all subsequences with n-1 length

If there are repetitions, we find the count of all distinct subsequences ending with the previous occurrence and remove them because the ones that end with the current character are the same when not appended the current character as the ones that don't end with the current character but then are appended this character

Time complexity: O(n)
Auxiliary space: O(n)

## (2) Map

```cpp
#include <iostream>
#include <map>
using namespace std;

int countSub(string s) {
    map<char, int> mp;

    int n = s.size();
    int allCount = 0, levelCount = 0;

    for (int i = 0; i < n; i++) {
        char c = s[i];

        if (i == 0) {
            allCount = levelCount = 1;
            mp[c] = 1; // Initialize the map with the first character
            continue;
        }

        levelCount = allCount + 1;

        if (mp.find(c) == mp.end()) {
            allCount += levelCount;
        } else {
            allCount += levelCount - mp[c];
        }
        mp[c] = levelCount; // Update the count for the current character
    }

    return allCount;
}

int main() {
    string list[] = {"abab", "gfg"};

    for (string s : list) {
        int cnt = countSub(s);
        int withEmptyString = cnt + 1;

        cout << "With empty string count for " << s << " is " << withEmptyString << endl;
        cout << "Without empty string count for " << s << " is " << cnt << endl;
    }
    return 0;
}
```


Explanation:

Time complexity: O(n)
Space complexity: O(1)

---
reference
(1) <https://www.geeksforgeeks.org/count-distinct-subsequences/>