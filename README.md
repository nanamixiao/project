# project

## Task 1

``` cpp

#include <iostream>
#include <vector>
#include <string>
#include <unordered_set>
using namespace std;


struct Player {
    string first_name;
    string last_name;
    string team;
};


vector<string> findPlayers(vector<Player> basketball_players, vector<Player> football_players) {
    unordered_set<string> names;
    vector<string> result;


    for (int i = 0; i < basketball_players.size(); i++) {
        string full_name = basketball_players[i].first_name + " " + basketball_players[i].last_name;
        names.insert(full_name);
    }


    for (int i = 0; i < football_players.size(); i++) {
        string full_name = football_players[i].first_name + " " + football_players[i].last_name;
        if (names.count(full_name)) {
            result.push_back(full_name);
        }
    }

    return result;
}


int main() {
    vector<Player> basketball_players = {
            {"Jill", "Huang", "Gators"},
            {"Janko", "Barton", "Sharks"},
            {"Wanda", "Vakulskas", "Sharks"},
            {"Jill", "Moloney", "Gators"},
            {"Luuk", "Watkins", "Gators"}
    };

    vector<Player> football_players = {
            {"Hanzla", "Radosti", "32ers"},
            {"Tina", "Watkins", "Barleycorns"},
            {"Alex", "Patel", "32ers"},
            {"Jill", "Huang", "Barleycorns"},
            {"Wanda", "Vakulskas", "Barleycorns"}
    };

    vector<string> both = findPlayers(basketball_players, football_players);


    for (int i = 0; i < both.size(); i++) {
        cout << both[i] << endl;
    }

    return 0;
}
```

## Task 2
``` cpp



#include <iostream>
#include <vector>
using namespace std;

int find(vector<int> nums) {

    int n = nums.size();

    int expected = n * (n + 1) / 2;

    int actual = 0;


    for (int i = 0; i < n; i++) {

        actual += nums[i];
    }


    return expected - actual;
}
int main() {

    vector<int> nums1 = {2, 3, 0, 6, 1, 5};
    vector<int> nums2 = {8, 2, 3, 9, 4, 7, 5, 0, 6};

    cout << "The missing number is " << find(nums1) << endl;
    cout << "The missing number is " << find(nums2) << endl;
    return 0;
}


```

## Task 3
``` cpp
#include <iostream>
#include <vector>
using namespace std;

int find(vector<int> nums) {



    int minNumber;
    int maxProfit;

    if (nums[0] > nums[1]){
        minNumber = nums[1];
        maxProfit = nums[0] - nums[1];
    } else {
        minNumber = nums[0];
        maxProfit = nums[1] - nums[0];
    }



    for (int i = 2; i < nums.size(); ++i) {
        int currentPrice = nums[i];


        int profit = currentPrice - minNumber;
        if (profit > maxProfit) {
            maxProfit = profit;
        }

        if (currentPrice < minNumber) {
            minNumber = currentPrice;
        }
    }

    return maxProfit;
}

int main() {
    vector<int> nums = {10, 7, 5, 8, 11, 2, 6};
    int result = find(nums);
    cout << "Maximum Profit is " << result << endl;
    return 0;
}
```


## Task 4
```CPP
#include <iostream>
#include <vector>
using namespace std;



int maxNum(vector<int>& nums) {


    int max1, max2;
    int min1, min2;


    if (nums[0] > nums[1]) {
        max1 = nums[0]; max2 = nums[1];
        min1 = nums[1]; min2 = nums[0];
    } else {
        max1 = nums[1]; max2 = nums[0];
        min1 = nums[0]; min2 = nums[1];
    }


    for (int i = 2; i < nums.size(); ++i) {
        int val = nums[i];

        if (val > max1) {
            max2 = max1;
            max1 = val;
        } else if (val > max2) {
            max2 = val;
        }

        if (val < min1) {
            min2 = min1;
            min1 = val;
        } else if (val < min2) {
            min2 = val;
        }
    }

    return max(max1 * max2, min1 * min2);
}


int main() {

    vector<int> nums = {5, -10, -6, 9, 4};

    int result = maxNum(nums);
    cout << "The maximum product of two number is " << result << endl;
    return 0;
}
```
## Task 5
``` cpp
#include <iostream>
#include <vector>
using namespace std;

vector<double> sortTemp(vector<double>& temps) {

    int count[21] = {0};


    for (int i = 0; i < temps.size(); i++) {
        double temp = temps[i];

        int index = (temp * 10) - 970;
        count[index] = count[index] + 1;
    }


    vector<double> sorted;
    for (int i = 0; i < 21; i++) {
        while (count[i] > 0) {
            double value = (970 + i) / 10.0;
            sorted.push_back(value);
            count[i] = count[i] - 1;
        }
    }

    return sorted;
}


int main() {

    vector<double> temp = {98.6, 98.0, 97.1, 99.0, 98.9, 97.8, 98.5, 98.2, 98.0, 97.1};

    vector <double> sortTemp1 = sortTemp(temp);
    for (int i = 0; i < size(temp); ++i) {

        cout << sortTemp1[i]<< " ";

    }
    cout << endl;


}




```
## Task 6
```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
using namespace std;

int find(vector<int>& nums) {
    unordered_set<int> a;

    for (int i = 0; i < nums.size(); i++) {
        a.insert(nums[i]);
    }

    int maxLength = 0;


    for (int i = 0; i < nums.size(); i++) {
        int num = nums[i];

        if (a.find(num - 1) == a.end()) {
            int currentNum = num;
            int count = 1;


            while (a.find(currentNum + 1) != a.end()) {
                currentNum++;
                count++;
            }

            if (count > maxLength) {
                maxLength = count;
            }
        }
    }

    return maxLength;
}



int main() {

}
```





