- 👋 Hi, I’m @ahmari22
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ... my game cool

<!---
ahmari22/ahmari22 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import time
import random

class Game:
    def __init__(self):
        self.player_health = 100
        self.inventory = []
        self.locations = ["abandoned club", "dark alley", "creepy record shop", "haunted studio"]
        self.current_location = "abandoned club"
    
    def start(self):
        print("Welcome to Echoes of Metro!")
        time.sleep(1)
        print("You are an aspiring music producer exploring a dark city.")
        time.sleep(1)
        self.explore()

    def explore(self):
        while self.player_health > 0:
            print(f"\nYou are at the {self.current_location}.")
            action = input("Do you want to (1) Explore, (2) Check Inventory, or (3) Leave? ")
            if action == "1":
                self.explore_location()
            elif action == "2":
                self.check_inventory()
            elif action == "3":
                print("You decided to leave the city. Game Over.")
                break
            else:
                print("Invalid action. Please choose again.")
        if self.player_health <= 0:
            print("You've succumbed to the darkness. Game Over.")

    def explore_location(self):
        if random.choice([True, False]):
            print("You hear a chilling echo of a beat...")
            self.encounter()
        else:
            print("The area is quiet, but you find an item.")
            self.find_item()

    def encounter(self):
        print("A shadowy figure appears! It looks like a distorted version of Metro.")
        action = input("Do you want to (1) Fight or (2) Run? ")
        if action == "1":
            print("You try to confront the figure...")
            if random.choice([True, False]):
                print("You survived the encounter but lost some health!")
                self.player_health -= 20
            else:
                print("The figure overpowers you. You are badly hurt!")
                self.player_health -= 50
        elif action == "2":
            print("You manage to escape, but not without leaving something behind.")
            if self.inventory:
                item = self.inventory.pop()
                print(f"You dropped a {item}.")
        else:
            print("Invalid action. You stand frozen in fear.")

    def find_item(self):
        item = "record"
        self.inventory.append(item)
        print(f"You found a {item}!")

    def check_inventory(self):
        if self.inventory:
            print("Your inventory contains:", ", ".join(self.inventory))
        else:
            print("Your inventory is empty.")

if __name__ == "__main__":
    game = Game()
    game.start()
    
