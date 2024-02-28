# To-do-list-
Minor project 
import json

def load_tasks():
    try:
        with open('tasks.json', 'r') as file:
            tasks = json.load(file)
    except FileNotFoundError:
        tasks = []
    return tasks

def save_tasks(tasks):
    with open('tasks.json', 'w') as file:
        json.dump(tasks, file)

def display_tasks(tasks):
    if tasks:
        print("Your To-Do List:")
        for idx, task in enumerate(tasks, start=1):
            print(f"{idx}. {task}")
    else:
        print("Your To-Do list is empty.")

def add_task(tasks, new_task):
    tasks.append(new_task)
    save_tasks(tasks)
    print("Task added successfully.")

def delete_task(tasks, index):
    try:
        del tasks[index]
        save_tasks(tasks)
        print("Task deleted successfully.")
    except IndexError:
        print("Invalid task index.")

def main():
    tasks = load_tasks()

    while True:
        print("\nTo-Do List Manager")
        print("1. View Tasks")
        print("2. Add Task")
        print("3. Delete Task")
        print("4. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            display_tasks(tasks)
        elif choice == '2':
            new_task = input("Enter the task: ")
            add_task(tasks, new_task)
        elif choice == '3':
            display_tasks(tasks)
            index = int(input("Enter the index of the task to delete: ")) - 1
            delete_task(tasks, index)
        elif choice == '4':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
    
