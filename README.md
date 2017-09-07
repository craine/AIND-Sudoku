# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: Constraint Propagation, in the case of Naked Twins, requires the constraint of each square reduce the search space. By enforce each constraint, we are able to see how it introduces new constraints for other parts of the board that can help us further reduce the number of possibilities. 

For Naked Twins the idea is taking the smallest number with twin values and compare those to the unit. Once it is determined that values were equal to other units we use constraint propagation by using one value (in image below it is 2,3) first is the 2. That number is added to row F3, for instance. Then the puzzle is run to see if it is solved. If it is not then 3 is used to solve the puzzle. The constraint allows us to then fill in the other values, if F3 = 2 then I3 must be 3. That is the constraint. If that is false, meaning did not solve the puzzle, then F3 = 3, therefore I3 must be 2. And, by the way, As these constraints are added it rules out 2 and 3 from D/E3. Thus D3/E3 are 79.


<img src="https://drive.google.com/uc?export=view&id=0B6Hft83pceJ9NnFvNHg0MjhMcmc" width="400" height="365"/>

A Counter was used to store values within the unit that were equal. Above example would have been 23 within any unit that matched those digits. The count was great than one it would remove any of those values that equal the naked twins, example above would be for D3/E3. Then using intersection function the values we identify boxes from the units that have those same numbers and remove them. Then we assign a value and run to see if puzzle is solved. 

<img src="https://drive.google.com/uc?export=view&id=0B6Hft83pceJ9N3BBdUt2QzQ4aWc" width="784" height="395"/>


Naked twins in used after eliminate and only-choice in reduce_puzzle in order to further reduce the number of possibilities before running the naked twins.

<img src="https://drive.google.com/uc?export=view&id=0B6Hft83pceJ9bm5MNXpFRjJlcE0" width="771" height="237"/>



was implemented in Python using a set intersection function. First we identify all boxes that have only 2 elements. Next we identify which boxes among these have the same elements to get naked twins. Once we get the naked twins, we remove the corresponding digits from all the boxes that are peers to both the twins. This is illustrated in the code snippet below.


# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: Diagonals were added to the cross function. The diagonals were set and added to the unitlist alongside the other units. We use the same constraint propagation method as we do for other portions of the code such as rows, columns and squares. Diagonal is one other constraint added in addition to those constraings. 

diag1 = [[str(r)+str(10- int(c)) for (r,c) in zip(rows,cols)]]
diag2 = [[r+c for (r,c) in zip(rows,cols)]]
unitlist = row_units + column_units + square_units + diag1 + diag2

### Install

This project requires **Python 3**.

We recommend students install [Anaconda](https://www.continuum.io/downloads), a pre-packaged Python distribution that contains all of the necessary libraries and software for this project. 
Please try using the environment we provided in the Anaconda lesson of the Nanodegree.

##### Optional: Pygame

Optionally, you can also install pygame if you want to see your visualization. If you've followed our instructions for setting up our conda environment, you should be all set.

If not, please see how to download pygame [here](http://www.pygame.org/download.shtml).

### Code

* `solution.py` - You'll fill this in as part of your solution.
* `solution_test.py` - Do not modify this. You can test your solution by running `python solution_test.py`.
* `PySudoku.py` - Do not modify this. This is code for visualizing your solution.
* `visualize.py` - Do not modify this. This is code for visualizing your solution.

### Visualizing

To visualize your solution, please only assign values to the values_dict using the `assign_value` function provided in solution.py

### Submission
Before submitting your solution to a reviewer, you are required to submit your project to Udacity's Project Assistant, which will provide some initial feedback.  

The setup is simple.  If you have not installed the client tool already, then you may do so with the command `pip install udacity-pa`.  

To submit your code to the project assistant, run `udacity submit` from within the top-level directory of this project.  You will be prompted for a username and password.  If you login using google or facebook, visit [this link](https://project-assistant.udacity.com/auth_tokens/jwt_login) for alternate login instructions.

This process will create a zipfile in your top-level directory named sudoku-<id>.zip.  This is the file that you should submit to the Udacity reviews system.

