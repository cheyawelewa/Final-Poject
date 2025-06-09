# Final-Poject
# Task 1


```cpp  
#include <iostream>  
#include <vector>  
#include <unordered_set>  
#include <string>  
  
struct Player {  
    std::string first_name;  
    std::string last_name;  
    std::string team;  
};  
  
std::vector<std::string> findPlayersInBothSports(const std::vector<Player>& basketball,   
                                                 const std::vector<Player>& football) {  
    std::unordered_set<std::string> basketball_full_names;  
    std::vector<std::string> common_players;  
      
    //Put all basketball players full names in hash set - O(N)  
    for (const Player& p : basketball) {  
        std::string name = p.first_name + " " + p.last_name;  
        basketball_full_names.insert(name);  
    }  
      
    //Check each football player against the set - O(M)  
    for (const Player& p : football) {  
        std::string name = p.first_name + " " + p.last_name;  
        if (basketball_full_names.count(name)) {  
            common_players.push_back(name);  
        }  
    }  
      
    return common_players;  
}  
  
int main() {  
    std::vector<Player> basketball = {  
        {"Jill", "Huang", "Gators"},  
        {"Janko", "Barton", "Sharks"},  
        {"Wanda", "Vakulskas", "Sharks"},  
        {"Jill", "Moloney", "Gators"},  
        {"Luuk", "Watkins", "Gators"}  
    };  
      
    std::vector<Player> football = {  
        {"Hanzla", "Radosti", "32ers"},  
        {"Tina", "Watkins", "Barleycorns"},  
        {"Alex", "Patel", "32ers"},  
        {"Jill", "Huang", "Barleycorns"},  
        {"Wanda", "Vakulskas", "Barleycorns"}  
    };  
      
    std::vector<std::string> both = findPlayersInBothSports(basketball, football);  
      
    std::cout << "Players who play both sports:" << std::endl;  
    for (const std::string& player_name : both) {  
        std::cout << player_name << std::endl;  
    }  
      
    return 0;  
}  
