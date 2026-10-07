# Task 1 — Programming & Data Handling

In this task, you will work with a drone dataset and learn the fundamentals of Python programming, data processing, data analysis, and data visualization.

Real-world robotic systems generate large amounts of operational, sensor, and telemetry data. Before this data can be used for applications such as monitoring, navigation, control, or machine learning, it needs to be properly understood, processed, and analyzed.

The goal of this task is to develop your basic programming and data-handling skills while working with data related to drone operations.

---

## 1. Dataset

For this task, you will work with the provided:

`dataset.csv`

The dataset is available in the same Task 1 folder as this task statement.

Download the dataset and place a copy inside your own `Task1` folder before beginning the task.

Before performing any analysis, first inspect the dataset and understand:

- What each column represents
- The type of values stored in each column
- Whether the dataset contains missing or unusual values
- What useful information can be obtained from the available attributes

Treat the dataset as raw data and determine how it should be processed before using it for analysis.

---

## 2. Python Fundamentals

Before working with the dataset, first learn and practice the basic concepts of Python programming.

### 2.1 Topics to Learn

You should be comfortable with the following concepts:

- Variables
- Basic data types
  - `int`
  - `float`
  - `str`
  - `bool`
- Taking user input
- Type conversion
- Arithmetic operators
- Comparison operators
- Logical operators
- Conditional statements
  - `if`
  - `elif`
  - `else`
- Loops
  - `for`
  - `while`
- Lists
- Tuples
- Dictionaries
- Indexing and slicing
- Basic list operations
- Functions
  - Function definition
  - Parameters
  - Return values
- Built-in functions such as:
  - `len()`
  - `min()`
  - `max()`
  - `sum()`
  - `range()`
- Basic string operations
- Reading from and writing to files
- Basic exception handling using:
  - `try`
  - `except`

---

### 2.2 Practice Questions

Complete the following questions before moving to the dataset analysis section.

#### Question 1 — Drone Sensor Analysis

Create separate lists containing sample readings for:

- Altitude
- Battery voltage
- Temperature

Write functions that can analyze any one of these sensor lists and determine:

- Minimum value
- Maximum value
- Average value
- Number of readings

Ask the user to choose which sensor data they want to analyze.

For the selected sensor:

- Display all readings
- Display the minimum, maximum, and average value
- Ask the user to enter a threshold
- Count how many readings are above or below the threshold, depending on the sensor
- Display a warning if the readings cross a limit that you consider unsafe

#### Question 2 — Drone Information Using Dictionary

Create a dictionary containing information about a drone, such as:

- Drone ID
- Model name
- Current altitude
- Battery percentage
- Flight mode

#### Question 3 — Flight Log File

Create a simple text file containing sample drone flight information.

Write a Python program that:

- Opens the file
- Reads the stored data
- Displays the contents
- Adds a new flight record to the file

Handle possible file-related errors using `try` and `except`.

---

## 3. Drone Data Analysis

Using the provided dataset, perform a complete basic data-analysis workflow in Python.

For this section, use:

- Pandas
- NumPy

### 3.1 Load and Explore the Dataset

- Load the CSV file using Pandas
- Display the first few rows
- Check the number of rows and columns
- Check the column names
- Check the data types of each column
- Generate basic statistical information for the numerical columns

### 3.2 Inspect the Dataset

Check the dataset for possible issues such as:

- Missing values
- Duplicate rows
- Incorrect data types
- Invalid or unrealistic values
- Sudden abnormal values or possible outliers

### 3.3 Clean and Preprocess the Dataset

Based on your observations, clean the dataset using suitable methods.

This may include:

- Removing duplicate rows
- Handling missing values
- Correcting data types
- Removing or replacing invalid values
- Sorting the data where required
- Performing any other preprocessing that you think is necessary

Save the final cleaned dataset as:

`cleaned_drone_data.csv`

### 3.4 Basic Analysis

Analyze the cleaned dataset and calculate useful information from the available numerical and categorical attributes.

This may include:

- Minimum values
- Maximum values
- Average values
- Counts and frequencies
- Comparison between different groups or categories
- Other useful statistics based on the available data

Also identify at least **two additional observations or patterns** from the dataset on your own.

You are encouraged to explore the dataset rather than limiting yourself only to the examples given above.

---

## 4. Data Visualization

Using the cleaned dataset, create meaningful visualizations to better understand and interpret the data.

For this section, use:

- Matplotlib
- Seaborn

Learn and use the following types of visualizations:

- Line Plot
- Scatter Plot
- Histogram
- Box Plot

You may also explore other suitable visualizations such as:

- Bar Plot
- Correlation Heatmap

Choose appropriate attributes/columns from the dataset for each visualization.

For every visualization:

- Decide which attribute or attributes should be used
- Choose an appropriate visualization
- Observe the resulting graph
- Explain what information, relationship, trend, distribution, or unusual behavior you can identify from it

Do not use plots only for displaying data.

The main objective is to interpret the visualization and extract useful information from it.

---

## 5. Folder Structure

Maintain a clear and organized folder structure for your task.

Your `Task1` folder should contain separate files for:

- Python fundamentals
- Data analysis
- Original dataset
- Cleaned dataset
- Visualizations
- Any additional files used in the task

Keep file and folder names meaningful and easy to understand.

For the data analysis section, you may use either:

- A Jupyter Notebook (`.ipynb`)
- A Python file (`.py`)

Recommended structure:

```text
Task1
│
├── python_basics.py
├── dataset.csv
├── drone_data_analysis.ipynb
├── cleaned_drone_data.csv
│
└── plots
    ├── plot1.png
    ├── plot2.png
    ├── plot3.png
    └── plot4.png
```

You may use a `.py` file instead of the notebook if preferred.

---

## 6. Learning Resources

Use the following resources to learn the concepts required for this task.

1. [Python Course](https://youtu.be/rfscVS0vtbw?si=mDZKu9zDugQE3q7r)
2. [NumPy Tutorial](https://youtu.be/QUT1VHiLmmI?si=vTBpvRXntEGsAQxJ)
3. [NumPy Tutorial](https://youtu.be/VXU4LSAQDSc?si=vDJSUWSC26FFWTR6)
4. [Pandas Tutorial](https://youtu.be/EhYC02PD_gc?si=b4N5kMgoFhwUXxOl)
5. [Pandas Tutorial](https://youtu.be/EXIgjIBu4EU?si=_k-rJH3fRbZ3179Q)
6. [Seaborn Tutorial](https://youtu.be/ooqXQ37XHMM?si=6EaIhnmKI6NEAu3i)
7. [Matplotlib Tutorial](https://youtu.be/7Lc2AxiM17o?si=0YUE1RlvnFGgLB3)

You are also encouraged to refer to the official documentation for:

- Python
- NumPy
- Pandas
- Matplotlib
- Seaborn

---

## 7. Submission

Complete the task inside the `Task1` folder of your personal task-phase GitHub repository.

Before submitting, ensure that your repository contains:

```text
Task1
│
├── python_basics.py
├── dataset.csv
├── drone_data_analysis.ipynb / drone_data_analysis.py
├── cleaned_drone_data.csv
│
└── plots
    ├── plot1.png
    ├── plot2.png
    ├── plot3.png
    └── plot4.png
```

Additional files created during the task may also be included.

Once your work is complete:

1. Commit and push the completed `Task1` folder to your GitHub repository.
2. Go to the official **Task-Phase repository**.
3. Open **Issues → New Issue → Task Submission**.
4. Select **Task 1**.
5. Fill in the required details.
6. Provide the direct GitHub link to your `Task1` folder.
7. Submit the Issue Form.

Do **not** upload your completed task directly to the central Task-Phase repository.

Your work should remain inside your own GitHub repository. The Issue Form is only used to submit the link for review.
