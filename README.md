CampusBite: Canteen Order Analytics

Course: Data Structures and Algorithms – 1 (26SC1203E)
Institution: KL University, Hyderabad
Project Type: Project-Based Learning (PBL) – Team of 3
Domain: Food & Campus Life

1. Project Title

CampusBite: Canteen Order Analytics

2. Abstract

CampusBite: Canteen Order Analytics is a data-analysis application that helps a campus canteen understand its UPI orders. Each order is stored in parallel arrays holding the order time, item ID, amount and UPI transaction ID, and test data is generated with a linear congruential generator so every run uses the same inputs.

The system answers six practical questions using core data structures and algorithms:

It detects double charges by finding repeated transaction IDs with a count array (O(n) instead of an O(n²) scan).
It suggests meal combos that fit a fixed budget using subset sum with memoisation.
It reports the revenue between any two times in O(1) using prefix sums.
It finds the busiest 30-minute lunch rush with a sliding window.
It counts the orders placed within a time slot using binary search.
It simulates the counter token queue to compare waiting times with one and two counters.

For selected features, brute-force and efficient versions are measured on growing inputs to show the effect of time complexity in practice. The project uses only synthetic data, with no real customer information.

3. Problem Statement

Campus canteens now take orders through UPI on a tablet. Every order is recorded, but the canteen manager has no simple way to make sense of the data. The manager wants to know:

Whether any customer has been charged twice because a payment app retried a transaction.
Which combination of items can be offered as a combo within a fixed budget.
How much revenue was earned between any two times of the day.
When the lunch rush happens.
How many orders were placed in a given time slot.
How long customers wait at the counter, and whether a second counter would help.

This project solves each of these problems efficiently using data structures and algorithms.

4. Objectives
Store and process canteen order data using arrays and strings.
Detect duplicate UPI transactions in linear time.
Build budget-friendly meal combos using memoisation.
Answer revenue queries between two times in constant time.
Identify the busiest 30-minute period of the day.
Count orders in a time slot using binary search.
Simulate the counter queue and compare waiting times.
Compare brute-force and efficient solutions and explain the difference using Big-O notation.
5. Features / Modules
No.	Module	Description
1	Catch Double Charges	Finds UPI transaction IDs that appear more than once.
2	Combo Builder	Picks menu items whose prices fit a Rs 150 budget as closely as possible.
3	Revenue Between Two Times	Returns the total revenue between any two time slots.
4	Find the Lunch Rush	Finds the busiest 30-minute window by revenue.
5	Orders in a Time Slot	Counts the orders placed in a given time range.
6	Counter Queue Simulation	Simulates the token queue and reports waiting times for 1 and 2 counters.
6. Algorithms and Complexity
Module	Technique	Course Week	Brute Force	Efficient
Catch Double Charges	Hashing / counting	Week 1	O(n²)	O(n)
Combo Builder	Memoisation (subset sum)	Week 4	O(2ⁿ)	O(n · B)
Revenue Between Two Times	Prefix sums	Week 5	O(n) per query	O(1) per query
Find the Lunch Rush	Sliding window	Week 7	O(n · k)	O(n)
Orders in a Time Slot	Binary search (lower bound)	Week 8	O(n)	O(log n)
Counter Queue Simulation	Queue (FIFO)	Week 12	–	O(T + n)

n = number of orders, B = budget, k = window size, T = simulated minutes

7. Tools and Technologies Used
Java (JDK 11)
Visual Studio Code
Java Extension Pack for Visual Studio Code
Git
GitHub
8. Project Structure
CampusBite-CanteenOrderAnalytics/
│
├── src/
│   └── Java source code
│
├── docs/
│   └── Project documentation, requirements and diagrams
│
├── data/
│   └── Sample order data and data generation details
│
├── results/
│   └── Program outputs, measurements and screenshots
│
├── reports/
│   └── Project review and final reports
│
├── lib/
│   └── Project libraries, if required
│
└── README.md
9. Working Principle
Generate order data: Synthetic orders are created using a linear congruential generator.
Store orders: Order time, item ID, amount and UPI transaction ID are stored in parallel arrays.
Display menu: The user chooses an analysis from the menu.
Check double charges: A count array finds repeated transaction IDs.
Build combos: A memo table finds the item combination closest to the budget.
Answer revenue queries: A prefix-sum array gives the revenue between two time slots instantly.
Find the rush: A sliding window moves over 10-minute totals to find the busiest 30 minutes.
Count orders in a slot: Two binary searches find the start and end of the time range.
Simulate the queue: Customers join a FIFO queue, and waiting times are calculated for 1 and 2 counters.
Display results: The output of each analysis is shown to the user.

The menu repeats until the user chooses Exit.

10. Setup Instructions
Install the Java Development Kit (JDK 11 or later).
Install Visual Studio Code.
Install the Java Extension Pack in Visual Studio Code.
Clone the repository from GitHub.
Open the project folder in Visual Studio Code.
Navigate to the src folder.
Open the main Java file.
Compile and run the program.
11. Execution Instructions
Open the project in Visual Studio Code.
Navigate to the src folder.
Open the main Java program.
Run the program.
Choose an option from the menu:
1 – Catch double charges
2 – Build a combo within budget
3 – Revenue between two times
4 – Find the lunch rush
5 – Orders in a time slot
6 – Counter queue simulation
7 – Exit
Enter the required input when prompted.
The program validates the input and displays the result.
Choose option 7 to exit the program.
12. Data

The data folder contains sample data used for testing and demonstrating CampusBite.

Each order record includes:

Time – minutes since 8:00 AM
Item ID – a number from 0 to 39
Amount – in rupees
UPI Transaction ID

The data is generated with the course's linear congruential generator, so the same inputs are produced on every run.

No real or personal customer information is used.

13. Results

The results folder contains the outputs generated by CampusBite, including program outputs, screenshots and performance measurements.

Sample outputs for the worked examples:

Module	Input	Output
Catch Double Charges	[501, 502, 503, 502, 504, 501, 505, 502]	repeats=3, distinct=5, first repeat=502
Combo Builder	Prices [60, 45, 30, 80, 25], budget 150	150
Revenue Between Two Times	Slots [450, 1200, 2300, 3100, 2800, 900, 600], queries [2,4], [0,6]	[8200, 11350]
Find the Lunch Rush	Same slots, window 3	sum=8200 starting at index 2
Orders in a Time Slot	Times [30, 95, 180, 241, 250, 266, 299, 300, 345], range [240, 300)	4
Counter Queue Simulation	Arrivals [1, 2, 1, 0, 2, 1, 0, 0], service 3 min, 1 counter	served=7, total wait=46 min, longest wait=13 min

For at least three modules, brute-force and efficient versions are compared on growing input sizes.

14. Documentation

The docs folder contains project-related documentation, including requirements, flowcharts, diagrams, algorithms and complexity analysis.

15. Reports

The reports folder contains project review documents, the project presentation and the final project report (3–4 pages).

16. Current Phase Status

The project is currently in the development phase.

The initial project structure, documentation and data generation have been set up. The modules are being developed week by week as each topic is covered in the course. Testing, performance measurements and further improvements will be added progressively throughout the project phases.

17. Version Control and Collaboration

Git and GitHub are used for version control and team collaboration.

Team contributions:

Member	Roll No.	Responsibility
Member 1	–	–
Member 2	–	–
Member 3	–	–

The project repository will be maintained throughout the project duration and will remain accessible until the final project evaluation.

18. Future Enhancements
Recommend a two-item combo whose prices add up to a budget, using two pointers.
Add spike alerts for minutes when orders exceed the previous 10-minute maximum, using a monotonic deque.
Build an interactive web dashboard using HTML, CSS and JavaScript.
Show charts for item sales and hourly revenue.
Connect to real canteen order data in a secure way.
Perform further testing and improvements.
19. Project Status

Status: Development in Progress
