# Artificial Intelligence Nanodegree
## Introductory Project: Diagonal Sudoku Solver

# Question 1 (Naked Twins)
Q: How do we use constraint propagation to solve the naked twins problem?  
A: Constraint Propagation, in the case of Naked Twins, requires the constraint of each square reduce the search space. By enforce each constraint, we are able to see how it introduces new constraints for other parts of the board that can help us further reduce the number of possibilities. 

For Naked Twins the idea is taking the smallest number with twin values and compare those to the unit. Once it is determined that values were equal to other units we use constraint propagation by using one value (in image below it is 2,3) first is the 2. That number is added to row F3, for instance. Then the puzzle is run to see if it is solved. If it is not then 3 is used to solve the puzzle. The constraint allows us to then fill in the other values, if F3 = 2 then I3 must be 3. That is the constraint. If that is false, meaning did not solve the puzzle, then F3 = 3, therefore I3 must be 2. And, by the way, As these constraints are added it rules out 2 and 3 from D/E3. Thus D3/E3 are 79.



<img src="https://drive.google.com/uc?export=view&id=0B6Hft83pceJ9NnFvNHg0MjhMcmc" width="100" height="100"/>




    for unit in unitlist:
        # count the number times that similar box occurs in a unit
        unitCounter = Counter([values[box] for box in unit])
        for boxTwins, count in unitCounter.items():
            # find all available boxes that are greater than 1
            if 1 < count == len(boxTwins):
                for box in unit:
                    # remove all values that exist for naked twins
                    if values[box] != boxTwins and set(values[box]).intersection(set(boxTwins)):
                        for digit in boxTwins:
                            values = assign_value(values, box, values[box].replace(digit, ''))
    return values


# Question 2 (Diagonal Sudoku)
Q: How do we use constraint propagation to solve the diagonal sudoku problem?  
A: *Student should provide answer here*

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

