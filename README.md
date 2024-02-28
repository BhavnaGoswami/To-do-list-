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
    
import json
from datetime import datetime

# Function to load tasks from JSON file
def load_tasks():
    try:
        with open('tasks.json', 'r') as file:
            tasks = json.load(file)
    except FileNotFoundError:
        tasks = []
    return tasks

# Function to save tasks to JSON file
def save_tasks(tasks):
    with open('tasks.json', 'w') as file:
        json.dump(tasks, file)

# Function to display tasks
def display_tasks(tasks):
    if tasks:
        print("Your To-Do List:")
        for idx, task in enumerate(tasks, start=1):
            print(f"{idx}. {task['title']} - Priority: {task['priority']} - Due Date: {task['due_date']}")
    else:
        print("Your To-Do list is empty.")

# Function to add a new task
def add_task(tasks):
    title = input("Enter the task title: ")
    priority = input("Enter the priority level (high/medium/low): ")
    due_date_str = input("Enter the due date (YYYY-MM-DD) or leave blank if none: ")
    if due_date_str:
        due_date = datetime.strptime(due_date_str, "%Y-%m-%d").date()
    else:
        due_date = None
    new_task = {'title': title, 'priority': priority, 'due_date': due_date}
    tasks.append(new_task)
    save_tasks(tasks)
    print("Task added successfully.")

# Function to delete a task
def delete_task(tasks, index):
    try:
        del tasks[index]
        save_tasks(tasks)
        print("Task deleted successfully.")
    except IndexError:
        print("Invalid task index.")

# Function to mark a task as completed
def mark_task_completed(tasks, index):
    try:
        tasks[index]['completed'] = True
        save_tasks(tasks)
        print("Task marked as completed.")
    except IndexError:
        print("Invalid task index.")

# Function to filter tasks by priority
def filter_by_priority(tasks, priority):
    filtered_tasks = [task for task in tasks if task['priority'].lower() == priority.lower()]
    display_tasks(filtered_tasks)

# Function to filter tasks by due date
def filter_by_due_date(tasks, due_date):
    filtered_tasks = [task for task in tasks if task['due_date'] == due_date]
    display_tasks(filtered_tasks)

# Function to search tasks by title
def search_tasks(tasks, query):
    filtered_tasks = [task for task in tasks if query.lower() in task['title'].lower()]
    display_tasks(filtered_tasks)

# Main function
def main():
    tasks = load_tasks()

    while True:
        print("\nTo-Do List Manager")
        print("1. View Tasks")
        print("2. Add Task")
        print("3. Delete Task")
        print("4. Mark Task as Completed")
        print("5. Filter by Priority")
        print("6. Filter by Due Date")
        print("7. Search Tasks")
        print("8. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            display_tasks(tasks)
        elif choice == '2':
            add_task(tasks)
        elif choice == '3':
            display_tasks(tasks)
            index = int(input("Enter the index of the task to delete: ")) - 1
            delete_task(tasks, index)
        elif choice == '4':
            display_tasks(tasks)
            index = int(input("Enter the index of the task to mark as completed: ")) - 1
            mark_task_completed(tasks, index)
        elif choice == '5':
            priority = input("Enter the priority level to filter by (high/medium/low): ")
            filter_by_priority(tasks, priority)
        elif choice == '6':
            due_date_str = input("Enter the due date to filter by (YYYY-MM-DD): ")
            due_date = datetime.strptime(due_date_str, "%Y-%m-%d").date()
            filter_by_due_date(tasks, due_date)
        elif choice == '7':
            query = input("Enter the search query: ")
            search_tasks(tasks, query)
        elif choice == '8':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")
           

from datetime import datetime



# Function to save tasks to JSON file
def save_tasks(tasks):
    with open('tasks.json', 'w') as file:
        json.dump(tasks, file)

# Function to display tasks
def display_tasks(tasks):
    if tasks:
        print("Your To-Do List:")
        for idx, task in enumerate(tasks, start=1):
            print(f"{idx}. {task['title']} - Priority: {task['priority']} - Due Date: {task['due_date']}")
    else:
        print("Your To-Do list is empty.")

# Function to add a new task
def add_task(tasks):
    title = input("Enter the task title: ")
    priority = input("Enter the priority level (high/medium/low): ")
    due_date_str = input("Enter the due date (YYYY-MM-DD) or leave blank if none: ")
    if due_date_str:
        due_date = datetime.strptime(due_date_str, "%Y-%m-%d").date()
    else:
        due_date = None
    new_task = {'title': title, 'priority': priority, 'due_date': due_date}
    tasks.append(new_task)
    save_tasks(tasks)
    print("Task added successfully.")

# Function to delete a task
def delete_task(tasks, index):
    try:
        del tasks[index]
        save_tasks(tasks)
        print("Task deleted successfully.")
    except IndexError:
        print("Invalid task index.")

# Function to mark a task as completed
def mark_task_completed(tasks, index):
    try:
        tasks[index]['completed'] = True
        save_tasks(tasks)
        print("Task marked as completed.")
    except IndexError:
        print("Invalid task index.")

# Function to filter tasks by priority
def filter_by_priority(tasks, priority):
    filtered_tasks = [task for task in tasks if task['priority'].lower() == priority.lower()]
    display_tasks(filtered_tasks)

# Function to filter tasks by due date
def filter_by_due_date(tasks, due_date):
    filtered_tasks = [task for task in tasks if task['due_date'] == due_date]
    display_tasks(filtered_tasks)

# Function to search tasks by title
def search_tasks(tasks, query):
    filtered_tasks = [task for task in tasks if query.lower() in task['title'].lower()]
    display_tasks(filtered_tasks)

# Main function
def main():
    tasks = load_tasks()

    while True:
        print("\nTo-Do List Manager")
        print("1. View Tasks")
        print("2. Add Task")
        print("3. Delete Task")
        print("4. Mark Task as Completed")
        print("5. Filter by Priority")
        print("6. Filter by Due Date")
        print("7. Search Tasks")
        print("8. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            display_tasks(tasks)
        elif choice == '2':
            add_task(tasks)
        elif choice == '3':
            display_tasks(tasks)
            index = int(input("Enter the index of the task to delete: ")) - 1
            delete_task(tasks, index)
        elif choice == '4':
            display_tasks(tasks)
            index = int(input("Enter the index of the task to mark as completed: ")) - 1
            mark_task_completed(tasks, index)
        elif choice == '5':
            priority = input("Enter the priority level to filter by (high/medium/low): ")
            filter_by_priority(tasks, priority)
        elif choice == '6':
            due_date_str = input("Enter the due date to filter by (YYYY-MM-DD): ")
            due_date = datetime.strptime(due_date_str, "%Y-%m-%d").date()
            filter_by_due_date(tasks, due_date)
        elif choice == '7':
            query = input("Enter the search query: ")
            search_tasks(tasks, query)
        elif choice == '8':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
    
