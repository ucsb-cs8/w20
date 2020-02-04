---
assigned: 2020-02-04 08:59
desc: matplotlib and visualizations
due: 2020-02-11 08:59
layout: lab
num: lab04
ready: true
---


In this lab, you'll continue practicing writing functions and testing them.
You will also see how to visualize data using the `matplotlib` package.

The tools you'll be creating will be useful in other courses and applicable to other disciplines, so we hope you have fun.

## Get started with `Matplotlib.pyplot`

Drawing plots is a good way to visualize data, so in this lab, you will get to learn how to use `Matplotlib.pyplot`. For more in-depth guides for using Matplotlib, take a look at their tutorials page <https://matplotlib.org/tutorials/index.html>.

Pyplot is a module of Matplotlib which provides simple functions to add plot elements like lines, images, text, etc. to the current axes in the current figure.


### Install `matplotlib`

First, let's install the module by typing the following command line in the Terminal:

```
pip3 install --user matplotlib
```

### Create {{page.num}}_plot.py

Open a new file in idle3 as before and type the following line to import the module.

```
import matplotlib.pyplot as plt
```

Save your file as **{{page.num}}_plot.py**.


### Visualize movie data

Let's look at a table consisting of movie statistics in the last 10 years (Source: [The Numbers](https://www.the-numbers.com) database). 

{:class="table table-bordered"}
| Year  | Number of movies made | Combined Worldwide box office (in 10<sup>7</sup> dollars) 
| --- | --- | --- 
| 2020 | 506 | 70 
| 2019 | 3,961 | 3769 
| 2018 | 3,885 | 3826 
| 2017 | 3,607 | 3789 
| 2016 | 3,506 | 3690 
| 2015 | 3,009 | 3597 
| 2014 | 1,514 | 2995 
| 2013 | 1,419 | 2972  
| 2012 | 1,494 | 3158 
| 2011 | 1,287 | 2742 
| 2010 | 1,251 | 2540  

For each column in the table, we want to create a list:

```python
year_list = [2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020]
num_movies = [1251, 1287, 1494, 1419, 1514, 3009, 3506, 3607, 3885, 3961, 506]
money_list = [2540, 2742, 3158, 2972, 2995, 3597, 3690, 3789, 3826, 3769, 70]
```

Now, there are two plots we want to show: one for number of movies vs. year, and the other for money vs. year. 
Remember that the convention of "vs." is y axis variable vs. x axis variable. However, when we call the `plt.plot` function to plot the graph, the _first_ parameter is the data of x axis variable and the _second_ parameter is the data of y axis variable. 

Therefore, to plot the number of movies vs. year plot, year should be on the x axis and number of movies should be on the y axis. 

Here's how to do it in code:

```python
plt.plot(year_list, num_movies)
```


In order to visualize this plot, add the following line:

```python
plt.show()
```


Similarity, to plot and visualize the graph of money vs. year, add the following two lines:

```python
plt.plot(year_list, money_list)
plt.show()
```

_Note that the second plot will show up after you close the first one._

This is the code you should have for now for showing two plots separately:
```python
import matplotlib.pyplot as plt

year_list = [2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020]
num_movies = [1251, 1287, 1494, 1419, 1514, 3009, 3506, 3607, 3885, 3961, 506]
money_list = [2540, 2742, 3158, 2972, 2995, 3597, 3690, 3789, 3826, 3769, 70]

plt.plot(year_list, num_movies)
plt.show()

plt.plot(year_list, money_list)
plt.show()
```

But what if we want to have both plots in the same graph?

We would remove the first `plt.show()` line, thus changing the code to the following:

```python
import matplotlib.pyplot as plt

year_list = [2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020]
num_movies = [1251, 1287, 1494, 1419, 1514, 3009, 3506, 3607, 3885, 3961, 506]
money_list = [2540, 2742, 3158, 2972, 2995, 3597, 3690, 3789, 3826, 3769, 70]

plt.plot(year_list, num_movies)

plt.plot(year_list, money_list)
plt.show()
```

To distinguish which plot represents what data, we need to add a legend that labels the plots. 
In order to do so, we want to label each plot when calling `plt.plot()` as follows:

```python
plt.plot(year_list, num_movies, label="number of movies")
plt.plot(year_list, money_list, label="money (in 10^7 dollars)")
```

In additionally, we need to add the legend which will create a legend on the plot using our labels:

```python
plt.legend()
```

Therefore, your code after above changes should be the following:

```python
import matplotlib.pyplot as plt

year_list = [2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020]
num_movies = [1251, 1287, 1494, 1419, 1514, 3009, 3506, 3607, 3885, 3961, 506]
money_list = [2540, 2742, 3158, 2972, 2995, 3597, 3690, 3789, 3826, 3769, 70]

plt.plot(year_list, num_movies, label="number of movies")
plt.plot(year_list, money_list, label="money (in 10^7 dollars)")
plt.legend()
plt.show()
```

Lastly, to add labels for the x axis, add the following line before `plt.show()`:

```python
plt.xlabel("Year")
```

Last but not least, let's add a simple title to our plot:
```python
plt.title("Movie Statistics")
```

Therefore, our final code is 

```python
import matplotlib.pyplot as plt

year_list = [2010, 2011, 2012, 2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020]
num_movies = [1251, 1287, 1494, 1419, 1514, 3009, 3506, 3607, 3885, 3961, 506]
money_list = [2540, 2742, 3158, 2972, 2995, 3597, 3690, 3789, 3826, 3769, 70]

plt.plot(year_list, num_movies, label="number of movies")
plt.plot(year_list, money_list, label="money (in 10^7 dollars)")
plt.legend()
plt.xlabel("Year")
plt.title("Movie Statistics")
plt.show()
```

That's it for plotting! Feel free to include additional data to visualize.

Please save your code in a file named **{{page.num}}_plot.py** and submit it in gradescope along with other files you complete in this lab. 


# Applications

Let us now switch gears and look at the financial application of what we are learning. Note that when you compute the savings and earnings using the functions below, you can use `matplotlib` to visualize the amounts per month and per year.
We will leave it up to you to play around with those in your **{{page.num}}_plot.py** file.


The following functions should be in a separate file called **{{page.num}}.py**.

## Applications : Continuously Compounded Interest

Suppose we decide to invest some money in an account that continously compounds interest. In other words, the amount that we initially invested is constantly earning interest and any interest that we earned also keeps acquiring interest.

At first, let's compute our earnings in the short term. Suppose you save $100 _each_ month into a savings account that has an annual interest rate of 5%. So, the monthly interest rate is $$ 0.05 / 12 = 0.00417 $$. After the first month, the value in the account becomes

$$ 100 * (1 + 0.00417) = 100.417 $$

After the second month, the value in the account becomes

$$ (100 + 100.417) * (1 + 0.00417) = 201.252 $$

After the third month, the value in the account becomes

$$ (100 + 201.252) * (1 + 0.00417) = 302.507 $$

and so on.

Before you begin writing any code, try writing out the pseudocode for your function. Think about how you would calculate the compound interest if you did the math by hand and use this to help you in the implementation. 


Write a function `savings` that computes and returns the savings amount after the given month, given a monthly contribution amount (e.g., 100), the annual interest rate (e.g., 5), and the number of months (e.g., 6), .

Use the `while` loop to implement this function.

```python
def savings(amount, interest_rate, months):
        '''
        Given a monthly contribution amount (e.g., 100), 
        the annual interest rate (e.g., 5), 
        and the number of months (e.g., 6), 
        returns the savings amount after 
        the given month.
        '''

        return "stub"   # TODO: replace return "stub" with a correct return statement
```

Now, write a new function `savingsByMonth()` that will save each month's savings as a new element in the list, which gets returned from the function. So, in the example above, the list would have the initial amount stored as the first element, 100.417 as the second element, etc.

```python
def savingsByMonth(amount, interest_rate, months):
        '''
        Given a monthly contribution amount (e.g., 100), 
        the annual interest rate (e.g., 5), 
        and the number of months (e.g., 6), 
        returns a list with the savings amount 
        for each month, including the initial amount
        as the first element, and the savings in
        the given month as the last element.
        '''

        return "stub"   # TODO: replace return "stub" with a correct return statement
```

Now that you have the list, you can switch to your **{{page.num}}_plot.py** and use the `matplotlib` package to visualize the earnings.

## Continuously Compounded Interest

The formula for _continously compounded interest_ is modeled by $$ A = Pe^{Rt} $$, where $$ A $$ is the amount earned, $$ P $$ is the _principal_, which is our initial investment, $$ e $$ is the Euler's constant, $$ R $$ is the annual rate of interest, and $$ t $$ is time in years.

```python
def compound_interest(principal, interest_rate, time):
        '''
        - Given an initial investment (principal),
        return the amount earned using the formula
        for continously compounded interest:
        A = P*e**(R*t), where 
        A = the amount earned,
        P = the principal (initial investment), 
        e = the Euler's constant, 
        R = the annual rate of interest, and
        t = time in years
        '''

        return "stub"   # TODO: replace return "stub" with a correct return statement
```

Suppose we decide to invest 50,000 dollars at the bank of CS8. The bank offers an interest rate of 8.0%. Assuming that our investment continously compounds interest, compute the amount of money earned after 10 years (use `import math` to be able to use `math.e`). 

As always, write pytest functions to verify that your function produces correct values.



## Progressive Taxation

Now that we've made so much money with our investment, it's time to pay taxes on it.

Write a function with a parameter `income` that calculates the amount of income tax owed according to the specified tax brackets below: 

{:class="table table-bordered"}
|   income cap   | marginal tax rate |
| -------------- |  ---------------  |
|     10000      |     0.00 (0%)     |
|     40000      |     0.12 (12%)    |
|     85000      |     0.22 (22%)    |
|     163000     |     0.24 (24%)    |
|     200000     |     0.32 (32%)    |
|     500000     |     0.35 (35%)    |
|   100000000    |     0.37 (37%)    |

### How Tax Brackets Work

A tax bracket is a range of income based on an income cap. Each bracket is taxed at a different marginal tax rate, meaning that only the part of your income that falls within a specific tax bracket gets taxed by the corresponding marginal tax rate for that tax bracket. 

For example, 
* if `income` = $150,000, the first $10,000 that fall in the tax bracket \[0, 10000] would be taxed at 0%, 
* the next $30,000 that fall in the tax bracket (10000, 40000] would be taxed at 12%, 
* the next $45,000 that fall in the tax bracket (40000, 85000) would be taxed at 22%, and 
* the remaining $65,000 that fall in the tax bracket (85000, 163000] would be taxed at 24%. 
    
    Your total tax owed would be the sum of the tax amounts at each tax bracket. So if `income` = $150,000, then tax owed = (30,000 * 0.12) + (45,000 * 0.22) + (65,000 * 0.24) = $29100.

For more information on how tax brackets work, read more [here](https://www.nerdwallet.com/blog/taxes/federal-income-tax-brackets/).

* This function could be implemented with a `while` loop or with a series of `if` or `if/elif/else` statements. You can decide how you want to implement the function. (_Note: you might find that this function is much more straight forward if you implement it using `if` statesments (or `if/elif/else`)._) 
* Before you begin writing any code, try writing out the pseudocode for your function. Think about how you would calculate the taxed owed if you did the math by hand and use this to help you in the implementation. 

```python
#income cap         marginal tax rate
# [0, 10000]           0.00 (0%)
# (10000, 40000]        0.12 (12%)
# (40000, 85000]        0.22 (22%)
# (85000, 163000]       0.24 (24%)
# (163000, 200000]      0.32 (32%)
# (200000, 500000]      0.35 (35%)
# (500000, 100000000]   0.37 (37%)

def tax(income):
        '''
        - Given an income amount as a whole number 
        where 0 <= income <= 100,000,000 , calculate 
        the amount of tax owed according to the tax brackets above.
        Return the total tax owed.
        - Example: if income = 70000, then 
        tax owed = 30000 * 0.12 + (income - 40000) * 0.22
        '''

        return "stub"   # TODO: replace return "stub" with a correct return statement
```

# Starter code for the practice function 

This is the end of the required/graded portion of the lab.

The functions below are designed to get you practicing using the concepts of `while` loops, conditionals, accumulator pattern, writing functions.


```python

def volleyballset():
        '''
        -This function roughly stimulates a volleyball game 
         between two teams. 
        -The team that reaches 25 points first wins.
        -The score is updated randomly through the use of the
         random number generator.
        -If the number generated is even, add one point to the first team.
        -If the number is odd, add one point to the second team.
        -Whichever team reaches 25 points first win.s
         print("team ___ wins with a score of " + score) 
         along with their score (which should be 25) 
         Also print the score of the losing team
        print("team ___ loses with a score of " + score) 
         along with their score.
        Hint: you need two different scores
        Hint: use a while loop to keep going until a team reaches 25
        Hint: use random number generator to generate a number 
        '''
        
def guessinggame():
        '''
        -This function stimulates a guessing game.
        -First, generate a random number between 0 and 100
        -Then prompt the user to enter a number 
         input("Enter a number between 0 and 100: ")
        -The user will keep guessing a number until 
         they correctly guess the one generated
        by the random number generator
        -If the number they guess is too low print 
         "Your number was too low. Try again!"
        -If the number they guess is too high print 
         "Your number was too high. Try again!"
        -Once they guess the right number print 
         "Good Job! You guessed the right number!"
        Hint: make sure you store the value that the user inputs 
        '''     

```  



## Final Step:  Log Out

**Acknowledgment**: Special thanks to Sara Mandic, April Sanchez, Radha Kumaran, and Sherry Chen who helped create this lab.


