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

int findMissingNumber(vector<int> nums) {
    int actual_sum = 0;
    int max_value = 0;

    for (int i = 0; i < nums.size(); i++) {
        actual_sum += nums[i];
        if (nums[i] > max_value) {
            max_value = nums[i];
        }
    }

    int expected_sum = (max_value * (max_value + 1)) / 2;
    int missing = expected_sum - actual_sum;
    return missing;
}

int main() {


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

}
```


## Task 4





