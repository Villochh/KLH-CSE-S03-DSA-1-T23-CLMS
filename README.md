# KLH-FED-2026-RainCatch
1. Project Title
  RainCatch: Rooftop Water Harvesting
A Java based application that helps housing societies estimate how much rainwater their terraces trap and plan pumping and tank capacity for the monsoon.

2. Team Members
   Aayush           2620030709
   Sriram Viloch    2620030127

3. Supervisor
   Mrs. Madhavi

4. Abstract

RainCatch is a sustainability project that helps housing societies plan rooftop rainwater harvesting. During the monsoon, societies need to know how much rain falls over a period, how much water their terraces can trap, how large a flat area is available for collection tanks and what pumping capacity they need to move the collected water in time. Estimating these by hand is slow and error-prone, and simple methods become too slow when the data grows.

The project solves this through six milestones, each using a data structures and algorithms technique taught in that week of the course: counting and hashing to classify rainfall days into bands, recursion (flood fill) to size a connected puddle on a terrace grid, prefix sums to answer rainfall-over-a-period queries, two pointers to compute the water trapped between terraces of different heights, binary search on the answer to find the minimum daily pumping capacity, and a monotonic stack to find the largest flat roof area. For each milestone, the expected time complexity is stated and the correctness of the algorithm is justified.

The input data consists of terrace heights along a row, daily rainfall in millimetres and a terrace grid. Synthetic data is generated using the course's linear congruential generator (LCG), so that every language version sees identical inputs. For at least three milestones, a brute-force version is compared with the efficient version by counting operations on growing inputs, showing how Big-O analysis predicts real performance. The project shows how fundamental algorithmic techniques can be applied to a real-world water conservation problem.

5. Objectives

- To classify daily rainfall into bands and find the most common band in O(n) time.
- To find the size of a connected flooded region on a terrace grid using recursion.
- To answer rainfall-over-a-period queries efficiently using prefix sums.
- To calculate the total water trapped between terraces using two pointers.
- To find the minimum daily pumping capacity using binary search on the answer.
- To find the largest flat roof area using a monotonic stack.
- To compare brute-force and efficient algorithms using operation counts.
- To apply data structures and algorithms to a real-world sustainability problem.

6. Features

- Rainfall band analysis (dry, light, moderate, heavy)
- Flooded region detection on a terrace grid
- Total rainfall over any range of days
- Calculation of water trapped between terraces
- Minimum pump capacity planning
- Largest flat roof area for tank placement
- Synthetic data generation using a linear congruential generator
- Automated tests for all worked examples and edge cases from a single main
- Brute force vs efficient performance measurements

7. Concepts Used

- Hashing and counting (count arrays)
- Big-O time complexity analysis
- Recursion (flood fill)
- Prefix sums
- Two pointers
- Binary search on the answer
- Monotonic stack
- Arrays and strings (arrays-first approach, with collection versions where natural)

8. Technologies Used

- Java (Java 11 compatible)
- Visual Studio Code
- Git
- GitHub

9. Data Model

- Terrace heights along a row – an integer array, where each value is the height of one terrace.
- Daily rainfall – an integer array of rainfall in millimetres for each day.
- Rainfall bands – an integer array with values 0 (dry) to 3 (heavy).
- Terrace grid – an array of strings, where '.' is an open cell that can hold water and '#' is a blocked cell.
- Collection amounts – an integer array of litres collected (×100), in order.

Synthetic data is generated using the course's linear congruential generator (LCG), so that the same seed produces identical inputs in Java, Python and C++.

10. Milestones

Milestone 1 (Week 1) – Rainfall Bands
Technique: Hashing / Counting, Big-O
Problem: Count the number of days in each rainfall band and find the most common band.
Algorithm: Use a count array of size 4. Go through the days once and increase the count for each day's band. Then scan the count array to find the band with the highest count and the number of distinct bands (bands with count > 0).
Complexity: O(n) time, O(k) space, where k = 4 bands. The brute-force version counts each band by scanning the whole array again, which takes O(n × k), or O(n²) when counting each value separately.
Proof idea: Every day is visited exactly once and adds 1 to exactly one band, so the final counts are exact.
Example:
  Input: [0, 1, 2, 3, 1, 0, 2, 3, 0]
  Output: most frequent = 0 (count 3), distinct = 4

Milestone 2 (Week 3) – Flooded Region
Technique: Recursion (Flood Fill)
Problem: Find the size of the connected puddle on a terrace grid starting from a given cell.
Algorithm: Starting from the given cell, recursively visit the four neighbouring cells (up, down, left, right). A cell is counted if it is inside the grid, is open ('.') and has not been visited before. Each visited cell is marked so it is not counted again.
Complexity: O(R × C) time, where R and C are the number of rows and columns, because each cell is visited at most once.
Proof idea: The recursion reaches every open cell connected to the start, and marking visited cells makes sure no cell is counted twice.
Example:
  Input: ["..#.", ".##.", "...#", "#..."], start (0, 0)
  Output: 9

Milestone 3 (Week 5) – Rainfall Over a Period
Technique: Prefix Sums
Problem: Answer many queries asking for the total rainfall between day L and day R.
Algorithm: Build a prefix array where prefix[i + 1] = prefix[i] + rain[i]. Each query is then answered as prefix[R + 1] − prefix[L]. A long (64-bit) type is used to avoid overflow.
Complexity: O(n + q) time, where n is the number of days and q is the number of queries. The brute-force version adds up each range separately, which takes O(n × q).
Proof idea: prefix[R + 1] holds the sum of days 0 to R and prefix[L] holds the sum of days 0 to L − 1, so their difference is exactly the sum of days L to R.
Example:
  Input: rainfall [0, 12, 35, 60, 8, 0, 22, 41], queries [[1, 4], [0, 7]]
  Output: [115, 178]

Milestone 4 (Week 6) – Water Trapped
Technique: Two Pointers
Problem: Find the total amount of water trapped between terraces of different heights.
Algorithm: Place one pointer at each end of the array and keep track of the highest terrace seen from the left (leftMax) and from the right (rightMax). Always move the pointer on the side with the smaller maximum. The water above that position is (that side's maximum − current height).
Complexity: O(n) time and O(1) extra space. The brute-force version finds the highest terrace on the left and right for every position, which takes O(n²).
Proof idea: The water above a terrace depends on the smaller of the highest terraces on its left and right. When leftMax is smaller than rightMax, the left side is the limit, so the water at the left pointer can be fixed safely, and the same applies to the right side.
Example:
  Input: [12, 4, 7, 2, 9, 3, 3, 15, 6, 8, 1, 10]
  Output: 59

Milestone 5 (Week 9) – Pump Capacity
Technique: Binary Search on the Answer
Problem: Find the minimum daily pumping capacity needed to move all collected water, in order, within a given number of days.
Algorithm: The answer lies between the largest single collection (low) and the total of all collections (high). For a candidate capacity, a greedy check fills each day in order until the next collection would exceed the capacity, then starts a new day. If the number of days needed is within the limit, try a smaller capacity; otherwise, try a larger one.
Complexity: O(n log S) time, where S is the total of all collections. The brute-force version tries every capacity one by one, which takes O(n × S).
Proof idea: If a capacity works, every larger capacity also works (the check is monotonic), so binary search finds the smallest capacity that works. The greedy check uses the fewest days for a given capacity, because packing each day as fully as possible never makes later days worse.
Example:
  Input: [12, 35, 60, 8, 22, 41, 18], 4 days
  Output: 60

Milestone 6 (Week 12) – Largest Flat Roof Area
Technique: Monotonic Stack
Problem: Find the largest rectangular flat area in a histogram of roof heights.
Algorithm: Keep a stack of indices with increasing heights. When a lower height is found, pop the higher bars. For each popped bar, its height is the rectangle's height and the width runs between the new top of the stack and the current index. Keep track of the largest area found.
Complexity: O(n) time, because each index is pushed and popped at most once. The brute-force version checks every pair of start and end positions, which takes O(n²).
Proof idea: When a bar is popped, the current index is the first lower bar to its right and the new stack top is the first lower bar to its left, so the widest rectangle using that bar's full height is found exactly once.
Example:
  Input: [2, 1, 5, 6, 2, 3]
  Output: 10

11. Complexity Summary

Milestone                  | Technique              | Brute Force | Efficient
1. Rainfall Bands          | Counting / Hashing     | O(n²)       | O(n)
2. Flooded Region          | Recursion (Flood Fill) | –           | O(R × C)
3. Rainfall Over a Period  | Prefix Sums            | O(n × q)    | O(n + q)
4. Water Trapped           | Two Pointers           | O(n²)       | O(n)
5. Pump Capacity           | Search on Answer       | O(n × S)    | O(n log S)
6. Largest Flat Roof Area  | Monotonic Stack        | O(n²)       | O(n)

12. Testing

All tests run automatically from a single main method. They include:
- Every worked example given above, compared against the expected output exactly.
- Edge cases such as:
  - Empty input
  - A single element
  - Duplicate values
  - All equal heights (no water trapped)
  - Strictly increasing or decreasing heights
  - A grid where the start cell is blocked
  - Large (overflow-sized) values, handled using long

13. Measurements

For at least three milestones (Rainfall Bands, Water Trapped and Largest Flat Roof Area), a brute-force version and the efficient version are run on growing input sizes generated with the LCG, using the doubling experiment from Week 1. The number of basic operations is counted for each input size.

When the input size doubles:
- O(n) algorithms take about twice as many operations.
- O(n²) algorithms take about four times as many operations.

These results match the Big-O analysis and show why the efficient versions are much faster on large inputs.

14. Setup Instructions
Install the Java Development Kit (JDK 11 or above).
Install Visual Studio Code.
Install the required Java extensions in Visual Studio Code.
Clone this repository from GitHub.
Open the project folder in Visual Studio Code.
Navigate to the src folder.
Open the main Java file.
Compile and run the program.

15. Execution Instructions
Open the project in Visual Studio Code.
Navigate to the src folder.
Open the main Java program.
Run the program.
The program runs every milestone on its worked example and prints the result next to the expected output.
The program runs the edge case tests and reports whether each one passes.
The program generates fresh synthetic data with the LCG and runs all milestones on it.
The program runs the brute force vs efficient measurements and prints the operation counts for growing input sizes.

16. Data

Synthetic data is generated using the course's linear congruential generator (LCG), so that Java, Python and C++ versions all see identical inputs for the same seed.

The data includes terrace heights, daily rainfall values, rainfall bands, terrace grids and collection amounts.

No real or sensitive personal information is used in this project.

17. Results

All six milestones produce the expected output for every worked example. Edge cases are handled correctly. The measurements show that the efficient algorithms grow as predicted by their Big-O complexity, while the brute-force versions become much slower as the input size increases.

18. Documentation

Project documentation includes the problem statement, the data model, the algorithm for each milestone with its complexity and proof idea, test cases and the measurement results.

19. Reports

Project reports include project review documents, the 3–4 page final project report and the demo material.

20. Current Phase Status

The project is currently in the development phase.

The milestones are being developed in week order, with each milestone using only the concepts taught by that week. Testing, measurements and documentation will be completed progressively throughout the 12-week project period.

21. Version Control and Collaboration

Git and GitHub are used for version control and team collaboration.

Each team member contributes using their own GitHub account so that individual contributions can be verified through the Git commit history.

The project repository will be maintained throughout the project duration and will remain accessible until the final project evaluation.

22. Future Enhancements
Find the number of days until heavier rain using a monotonic stack.
Find the wettest week using a sliding window.
Implement the project in a second language (Python or C++).
Use real rainfall data from weather records.
Add a graphical interface to show terraces, trapped water and puddles visually.
Estimate the tank size needed for a full monsoon season.

23. Project Status

Status: Development in Progress
