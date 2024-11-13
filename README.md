# Project-1
# This function loads the tasks from a text file
def load_tasks(filename="todo_list.txt"):
    try:
        # Try to open the file and read its contents
        file = open(filename, "r")  # "r" means read mode
        tasks = file.readlines()  # Reads each line in the file as an item in a list
        file.close()  # Don't forget to close the file when you're done
        # Remove any extra spaces or newlines from the tasks
        return [task.strip() for task in tasks]  # Return the cleaned list of tasks
    except FileNotFoundError:
        # If the file doesn't exist, return an empty list
        return []

# This function saves a new task to the text file
def save_task(task, filename="todo_list.txt"):
    file = open(filename, "a")  # "a" means append mode, so we don't erase existing tasks
    file.write(task + "\n")  # Add the task followed by a new line
    file.close()  # Close the file when done

# This function displays all the tasks in the list
def display_tasks(tasks):
    if len(tasks) == 0:
        print("Your to-do list is empty!")
    else:
        print("Here are your tasks:")
        for i in range(len(tasks)):
            print(f"{i + 1}. {tasks[i]}")  # Print each task with its number

# Main part of the program
def main():
    # First, load any tasks that are already saved in the file
    tasks = load_tasks()


# Start the program
if __name__ == "__main__":
    main()
