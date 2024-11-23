import random  # Import the random module to use for generating random numbers.

# Initialize the player's and computer's health to 100.
player_health = 100
computer_health = 100

# Display the available moves to the player.
print("\nYou and the computer can use these moves:")
print("1. Strike: Moderate damage (18-25)")
print("2. Power Strike: Big damage, but unpredictable (10-35)")
print("3. Heal: Heals yourself (18-25)\n")

# Start a loop that runs until either the player or the computer's health is 0.
while player_health > 0 and computer_health > 0:
    # Display current health of both the player and computer.
    print(f"\nYour health: {player_health}, Computer's health: {computer_health}")
    print("Your Turn! Choose your move:")
    print("1. Strike")
    print("2. Power Strike")
    print("3. Heal")

    try:
        # Ask the player to choose a move (1, 2, or 3).
        move = int(input("Enter 1, 2, or 3: "))
    except ValueError:  # Handle invalid input (if the player enters something that's not a number).
        print("Invalid choice! Please enter a number.")
        continue  # Skip to the next iteration of the loop.

    # Check which move the player chose and execute its effects.
    if move == 1:  # Player chose Strike.
        damage = random.randint(18, 25)  # Generate random damage between 18 and 25.
        computer_health -= damage  # Subtract the damage from the computer's health.
        print(f"You used Strike! You dealt {damage} damage.")  # Inform the player of the result.
    elif move == 2:  # Player chose Power Strike.
        damage = random.randint(10, 35)  # Generate random damage between 10 and 35.
        computer_health -= damage  # Subtract the damage from the computer's health.
        print(f"You used Power Strike! You dealt {damage} damage.")  # Inform the player of the result.
    elif move == 3:  # Player chose Heal.
        heal = random.randint(18, 25)  # Generate random healing between 18 and 25.
        player_health = min(player_health + heal, 100)  # Add healing to the player's health, but don't exceed 100.
        print(f"You used Heal Pulse! You healed {heal} health.")  # Inform the player of the result.
    else:  # If the player enters a number other than 1, 2, or 3.
        print("Invalid choice! Please pick 1, 2, or 3.")
        continue  # Skip to the next iteration of the loop.

    # Check if the computer's health has dropped to 0 or below.
    if computer_health <= 0:
        print("\nThe computer fainted. You win!")  # Announce the player's victory.
        break  # Exit the loop since the game is over.

    # Computer's turn to make a move.
    print("\nComputer's Turn!")
    if computer_health <= 35 and random.random() < 0.6:  # If the computer's health is low, increase chance to heal.
        move = 3  # The computer chooses Heal.
    else:
        move = random.choice([1, 2])  # Otherwise, randomly choose Strike or Power Strike.

    # Check the computer's chosen move and execute its effects.
    if move == 1:  # Computer chose Strike.
        damage = random.randint(18, 25)  # Generate random damage between 18 and 25.
        player_health -= damage  # Subtract the damage from the player's health.
        print(f"The computer used Strike! It dealt {damage} damage.")  # Inform the player of the result.
    elif move == 2:  # Computer chose Power Strike.
        damage = random.randint(10, 35)  # Generate random damage between 10 and 35.
        player_health -= damage  # Subtract the damage from the player's health.
        print(f"The computer used Power Strike! It dealt {damage} damage.")  # Inform the player of the result.
    elif move == 3:  # Computer chose Heal.
        heal = random.randint(18, 25)  # Generate random healing between 18 and 25.
        computer_health = min(computer_health + heal, 100)  # Add healing to the computer's health, capped at 100.
        print(f"The computer used Heal! It healed {heal} health.")  # Inform the player of the result.

    # Check if the player's health has dropped to 0 or below.
    if player_health <= 0:
        print("\nYou fainted. The computer wins!")  # Announce the computer's victory.
        break  # Exit the loop since the game is over.
