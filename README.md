README.md

Project Title: RainCatch: Rooftop Water Harvesting

Team No: KLH/DSA-1/S03/T__

Team Member Names & ID Numbers:
   1. 2620030709 – Aayush
   2. 2620030127 – Sriram Viloch

Supervisor's Name: Dr. Madhavi Karumudi

Abstract:
RainCatch is a Java-based project that helps housing societies plan rooftop rainwater harvesting for the monsoon. It estimates how much rain their terraces can trap and helps plan pumping and tank capacity. The project is built through six milestones, each using a data structures and algorithms technique: counting and hashing to group rainfall days into bands, recursion (flood fill) to find the size of a puddle on a terrace grid, prefix sums to find rainfall over a period, two pointers to calculate the water trapped between terraces, binary search on the answer to find the minimum pump capacity, and a monotonic stack to find the largest flat roof area. Synthetic data is generated using a linear congruential generator. Brute-force and efficient versions are compared using operation counts to show how Big-O analysis predicts performance.

Project Structure:
RainCatch: Rooftop Water Harvesting (under this folder)
   |-- README.md
   |-- src
   |     |__ RainCatch.java (all source files)
   |-- docs
   |     |__ Abstract.pdf, Review PPTs
   |-- data
   |-- results
   |-- reports

Git Commands:
git init
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
git add .
git commit -m "Initial commit: RainCatch project structure"
git branch -M main
git remote add origin https://github.com/<username>/RainCatch.git
git push -u origin main
git status
git log
git pull origin main
