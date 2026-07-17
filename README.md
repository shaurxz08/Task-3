# Task-3
expenses = []

while True:
    print("\n====== Expense Tracker 2.0 ======")
    print("1. Add Expense")
    print("2. View Expenses")
    print("3. Search by Category")
    print("4. Category Total")
    print("5. Monthly Total")
    print("6. Exit")

    choice = input("Enter your choice: ")

    if choice == "1":
        desc = input("Enter Expense Description: ")
        amount = float(input("Enter Amount: "))
        category = input("Enter Category (Food/Travel/Shopping): ")
        month = input("Enter Month (YYYY-MM): ")

        expenses.append({
            "description": desc,
            "amount": amount,
            "category": category,
            "month": month
        })

        print("Expense Added Successfully!")

    elif choice == "2":
        print("\n----- All Expenses -----")
        if len(expenses) == 0:
            print("No expenses found.")
        else:
            for e in expenses:
                print(
                    f"{e['description']} | ₹{e['amount']} | "
                    f"{e['category']} | {e['month']}"
                )

    elif choice == "3":
        cat = input("Enter Category: ")
        found = False

        print("\nMatching Expenses:")
        for e in expenses:
            if e["category"].lower() == cat.lower():
                print(
                    f"{e['description']} | ₹{e['amount']} | "
                    f"{e['category']} | {e['month']}"
                )
                found = True

        if not found:
            print("No matching expenses found.")

    elif choice == "4":
        cat = input("Enter Category: ")
        total = 0

        for e in expenses:
            if e["category"].lower() == cat.lower():
                total += e["amount"]

        print(f"Total spent on {cat}: ₹{total}")

    elif choice == "5":
        month = input("Enter Month (YYYY-MM): ")
        total = 0

        for e in expenses:
            if e["month"] == month:
                total += e["amount"]

        print(f"Monthly Total for {month}: ₹{total}")

    elif choice == "6":
        print("Thank you!")
        break

    else:
        print("Invalid Choice!")
