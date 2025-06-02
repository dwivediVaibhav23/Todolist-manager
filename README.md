# Todolist-manager
#using Python
# To-Do List Manager: A simple Python program to manage tasks

def display_menu():
    """Display the menu options for the To-Do List Manager.""" 
    print("\n=== To-Do List Manager ===")
    print("1. View Tasks")
    print("2. Add Task")
    print("3. Mark Task Complete")
    print("4. Remove Task")
    print("5. Exit")
    print("==========================")

def view_tasks(tasks):
    """Display all tasks with their status (Pending/Completed)."""
    if not tasks:
        print("\nNo tasks in your list!")
        return
    print("\nYour Tasks:")
      
       # Enumerate starts counting from 1 for user-friendly task numbers
    
    for i, task in enumerate(tasks, 1):
        status = "Completed" if task["completed"] else "Pending"
        print(f"{i}. {task['name']} - {status}")

def add_task(tasks, task_name):
    """Add a new task to the list."""
    # Check for non-empty task name
    if task_name.strip():
        tasks.append({"name": task_name.strip(), "completed": False})
        print(f"\nTask '{task_name}' added!")
    else:
        print("\nError: Task name cannot be empty!")

def mark_task_complete(tasks, task_index):
    """Mark a task as completed by its index."""
    # Validate task index
    if 1 <= task_index <= len(tasks):
        tasks[task_index - 1]["completed"] = True
        print(f"\nTask '{tasks[task_index - 1]['name']}' marked as completed!")
    else:
        print("\nError: Invalid task number!")

def remove_task(tasks, task_index):
    """Remove a task from the list by its index."""
    # Validate task index
    if 1 <= task_index <= len(tasks):
        task_name = tasks.pop(task_index - 1)["name"]
        print(f"\nTask '{task_name}' removed!")
    else:
        print("\nError: Invalid task number!")

def main():
    """Main function to run the To-Do List Manager."""
    # Initialize empty task list
    tasks = []

    while True:
        display_menu()
        # Get user choice and remove whitespace
        choice = input("\nEnter choice (1-5): ").strip()

        if choice == "1":
            view_tasks(tasks)

        elif choice == "2":
            task_name = input("Enter task name: ")
            add_task(tasks, task_name)

        elif choice == "3":
            view_tasks(tasks)
            # Only prompt if tasks exist
            if tasks:
                try:
                    # Convert input to integer for task index
                    task_index = int(input("Enter task number to mark complete: "))
                    mark_task_complete(tasks, task_index)
                except ValueError:
                    print("\nError: Please enter a valid number!")

        elif choice == "4":
            view_tasks(tasks)
            # Only prompt if tasks exist
            if tasks:
                try:
                
                        # Convert input to integer for task index
               
                    task_index = int(input("Enter task number to remove: "))
                    remove_task(tasks, task_index)
                except ValueError:
                    print("\nError: Please enter a valid number!")

        elif choice == "5":
            print("\nThanks for using To-Do List Manager! Bye!")
            break

        else:
            print("\nError: Please choose a number between 1 and 5!")

# Run the program only if executed directly
if __name__ == "__main__":
    main()
