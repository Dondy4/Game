# Game
fun
def intro():
    print("Welcome to the Text Adventure!")
    print("You find yourself in a dark, damp cave.")

def game_loop():
    current_room = "cave"
    while True:
        if current_room == "cave":
            print("You're in a dark, damp cave.")
            print("You can go 'north' or 'east'.")
            choice = input("> ")
            if choice == "north":
                current_room = "forest"
            elif choice == "east":
                current_room = "dragon_lair"
            else:
                print("Invalid choice.")
        elif current_room == "forest":
            print("You're in a dense, mysterious forest.")
            print("You can go 'south' or 'west'.")
            # ... (similar to the cave)
        elif current_room == "dragon_lair":
            print("You've stumbled upon a dragon's lair!")
            print("Do you 'fight' or 'flee'?")
            # ... (game over or victory conditions)
        else:
            print("You've reached an unknown location.")
            break

health = 100

def damage_player(amount):
    global health
    health -= amount
    print(f"You lost {amount} health. Your health is now {health}.")

def heal_player(amount):
    global health
    health += amount
    print(f"You healed {amount} health. Your health is now {health}.")
    inventory = []

def add_to_inventory(item):
    inventory.append(item)
    print(f"You picked up a {item}!")

def check_inventory():
    if not inventory:
        print("Your inventory is empty.")
    else:
        print("Your inventory:")
        for item in inventory:
            print(f"- {item}")def combat(enemy_health):
    while enemy_health > 0 and health > 0:
        print(f"Enemy health: {enemy_health}")
        print(f"Your health: {health}")
        action = input("What do you do? (attack/flee) ")
        if action == "attack":
            enemy_health -= 20
            print("You attacked the enemy!")
        elif action == "flee":
            print("You fled the battle!")
            break
        else:
            print("Invalid action.")
        if enemy_health > 0:
            damage_player(10)
            print("The enemy attacked you!")

    if enemy_health <= 0:
        print("You defeated the enemy!")
    else:
        print("You lost the battle!")
