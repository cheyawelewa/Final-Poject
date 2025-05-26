# Final-Poject
# Task 1


#include <iostream>
#include <vector>
#include <unordered_set>
#include <string>

struct Player {
    std::string first_name;
    std::string last_name;
    std::string team;
};

std::vector<std::string> findPlayersInBothSports(const std::vector<Player>& basketball_players, 
                                                 const std::vector<Player>& football_players) {
    std::unordered_set<std::string> basketball_names;
    std::vector<std::string> result;
    
    //Put all basketball players full names in hash set - O(N)
    for (const auto& player : basketball_players) {
        std::string full_name = player.first_name + " " + player.last_name;
        basketball_names.insert(full_name);
    }
    
    //Check each football player against the set - O(M)
    for (const auto& player : football_players) {
        std::string full_name = player.first_name + " " + player.last_name;
        if (basketball_names.find(full_name) != basketball_names.end()) {
            result.push_back(full_name);
        }
    }
    
    return result;
}

int main() {
    std::vector<Player> basketball_players = {
        {"Jill", "Huang", "Gators"},
        {"Janko", "Barton", "Sharks"},
        {"Wanda", "Vakulskas", "Sharks"},
        {"Jill", "Moloney", "Gators"},
        {"Luuk", "Watkins", "Gators"}
    };
    
    std::vector<Player> football_players = {
        {"Hanzla", "Radosti", "32ers"},
        {"Tina", "Watkins", "Barleycorns"},
        {"Alex", "Patel", "32ers"},
        {"Jill", "Huang", "Barleycorns"},
        {"Wanda", "Vakulskas", "Barleycorns"}
    };
    
    auto dual_sport_players = findPlayersInBothSports(basketball_players, football_players);
    
    std::cout << "Players who play both sports:" << std::endl;
    for (const auto& name : dual_sport_players) {
        std::cout << name << std::endl;
    }
    
    return 0;
}
