import pandas as pd

# Load CSV file (replace 'your_file.csv' with your actual file path)
df = pd.read_csv('/content/Advance Rent - Draft.csv', thousands=',')  # Handles comma-formatted numbers

def compare_rent():
    # Get user input for branches
    branch1 = input("Enter first branch name: ").strip()
    branch2 = input("Enter second branch name: ").strip()

    # Get data for both branches
    try:
        rent1 = df[df['BRANCH'] == branch1]['MONTHLY RENT'].values[0]
        rent2 = df[df['BRANCH'] == branch2]['MONTHLY RENT'].values[0]
    except IndexError:
        print("Error: One or both branches not found")
        return

    # Calculate and display difference
    difference = abs(rent1 - rent2)
    print(f"\nRent Comparison:")
    print(f"{branch1}: {rent1:,.2f}")
    print(f"{branch2}: {rent2:,.2f}")
    print(f"Difference: {difference:,.2f}")

# Execute the comparison
compare_rent()
