# gse301-python-project
GSE301 Dataset Management and Basic Analysis System
# Part 1: Variables & File Handling

data = []  # this list will store numerical values

file = open("numbers.txt", "r")

for line in file:
    number = float(line.strip())
    data.append(number)

file.close()

print(data)
# Part 1 & Part 2: File Handling + Error Handling

data = []   # list to store numbers

try:
    file = open("numbers.txt", "r")

    for line in file:
        try:
            number = float(line.strip())   # convert text to number
            data.append(number)
        except ValueError:
            print("Invalid (non-numeric) value skipped.")

    file.close()

except FileNotFoundError:
    print("File not found.")
    data = []

# Check if file is empty or invalid
if len(data) == 0:
    print("File is empty or contains no valid numbers.")
else:
    print("Data loaded successfully:")
    print(data)
    # Part 3: Functions to calculate statistics

def calculate_total(data):
    total = 0
    for value in data:
        total += value
    return total


def calculate_average(data):
    total = calculate_total(data)
    average = total / len(data)
    return average


def calculate_minimum(data):
    minimum = data[0]
    for value in data:
        if value < minimum:
            minimum = value
    return minimum


def calculate_maximum(data):
    maximum = data[0]
    for value in data:
        if value > maximum:
            maximum = value
    return maximum
    # Part 4: Operators & Loops

total = 0
count = 0
minimum = data[0]
maximum = data[0]

for value in data:
    total = total + value        # using +
    count = count + 1            # counting elements

    if value < minimum:          # using <
        minimum = value

    if value > maximum:          # using >
        maximum = value

average = total / count          # using /
# Part 5: Conditional Statements

threshold = 70

if average >= threshold:
    print("High Performance")
else:
    print("Needs Improvement")
    # Part 6: Sets (Unique Categories)

categories = set()   # empty set to store unique values

try:
    file = open("categories.txt", "r")

    for line in file:
        category = line.strip()
        if category != "":
            categories.add(category)

    file.close()

except FileNotFoundError:
    print("Category file not found.")

print("Unique Categories:", categories)
print("Total Unique Categories:", len(categories))
# Part 7: Object-Oriented Programming (OOP)

class DataSet:
    def __init__(self, number_file, category_file):
        self.number_file = number_file
        self.category_file = category_file
        self.data = []
        self.categories = set()

        self.total = 0
        self.average = 0
        self.minimum = 0
        self.maximum = 0

    # Load numerical data and categories
    def load_data(self):
        # Load numerical data
        try:
            file = open(self.number_file, "r")

            for line in file:
                try:
                    number = float(line.strip())
                    self.data.append(number)
                except ValueError:
                    print("Invalid (non-numeric) value skipped.")

            file.close()

        except FileNotFoundError:
            print("Number file not found.")
            return False

        if len(self.data) == 0:
            print("Number file is empty or contains no valid numbers.")
            return False

        # Load categorical data
        try:
            file = open(self.category_file, "r")

            for line in file:
                category = line.strip()
                if category != "":
                    self.categories.add(category)

            file.close()

        except FileNotFoundError:
            print("Category file not found.")

        return True

    # Calculate total, average, minimum, maximum using loops and operators
    def calculate_statistics(self):
        self.total = 0
        self.minimum = self.data[0]
        self.maximum = self.data[0]
        count = 0

        for value in self.data:
            self.total = self.total + value
            count = count + 1

            if value < self.minimum:
                self.minimum = value

            if value > self.maximum:
                self.maximum = value

        self.average = self.total / count

    # Display results and performance message
    def display_results(self):
        print("Total:", self.total)
        print("Average:", self.average)
        print("Minimum:", self.minimum)
        print("Maximum:", self.maximum)

        # Performance check
        threshold = 70
        if self.average >= threshold:
            print("High Performance")
        else:
            print("Needs Improvement")

        print("Unique Categories:", self.categories)
        print("Total Unique Categories:", len(self.categories))


# Create object and run program
dataset = DataSet("numbers.txt", "categories.txt")

if dataset.load_data():
    dataset.calculate_statistics()
    dataset.display_results()
    # Dataset Management and Basic Analysis System

class DataSet:
    def __init__(self, number_file, category_file):
        self.number_file = number_file
        self.category_file = category_file
        self.data = []
        self.categories = set()

        self.total = 0
        self.average = 0
        self.minimum = 0
        self.maximum = 0
        self.performance = ""

    # Load numerical data and categories
    def load_data(self):
        # Load numerical data
        try:
            file = open(self.number_file, "r")

            for line in file:
                try:
                    number = float(line.strip())
                    self.data.append(number)
                except ValueError:
                    print("Invalid (non-numeric) value skipped.")

            file.close()

        except FileNotFoundError:
            print("Number file not found.")
            return False

        if len(self.data) == 0:
            print("Number file is empty or contains no valid numbers.")
            return False

        # Load categorical data
        try:
            file = open(self.category_file, "r")

            for line in file:
                category = line.strip()
                if category != "":
                    self.categories.add(category)

            file.close()

        except FileNotFoundError:
            print("Category file not found.")

        return True

    # Calculate statistics
    def calculate_statistics(self):
        self.total = 0
        self.minimum = self.data[0]
        self.maximum = self.data[0]
        count = 0

        for value in self.data:
            self.total = self.total + value
            count = count + 1

            if value < self.minimum:
                self.minimum = value

            if value > self.maximum:
                self.maximum = value

        self.average = self.total / count

        # Performance condition
        threshold = 70
        if self.average >= threshold:
            self.performance = "High Performance"
        else:
            self.performance = "Needs Improvement"

    # Display results
    def display_results(self):
        print("Total:", self.total)
        print("Average:", self.average)
        print("Minimum:", self.minimum)
        print("Maximum:", self.maximum)
        print("Performance:", self.performance)
        print("Unique Categories:", self.categories)
        print("Total Unique Categories:", len(self.categories))

    # Save results into a report file
    def save_report(self):
        file = open("report.txt", "w")

        file.write("DATASET ANALYSIS REPORT\n")
        file.write("------------------------\n")
        file.write("Total: " + str(self.total) + "\n")
        file.write("Average: " + str(self.average) + "\n")
        file.write("Minimum: " + str(self.minimum) + "\n")
        file.write("Maximum: " + str(self.maximum) + "\n")
        file.write("Performance: " + self.performance + "\n")
        file.write("Total Unique Categories: " + str(len(self.categories)) + "\n")

        file.close()
        print("Report saved to report.txt")


# Run the program
dataset = DataSet("numbers.txt", "categories.txt")

if dataset.load_data():
    dataset.calculate_statistics()
    dataset.display_results()
    dataset.save_report()
