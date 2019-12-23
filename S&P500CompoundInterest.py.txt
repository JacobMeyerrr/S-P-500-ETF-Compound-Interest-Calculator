# S&P500CompoundInterest.py
#
# Created by Jacob Meyer on 11/28/2019
# University of Minnesota Aerospace Engineering Junior
# Created on the "Python Programming Interpreter" iPhone app
#
# Tells you your net worth (in addition to income and % invested) depending
# on how much money you invest into a typical S&P 500 ETF (e.g. IVV or VOO)
# over a long period of time (years or decades).
#
# Good rule of thumb: Keep your money in there for at least 10 years (likely
# many more) since the S&P 500 is a long-term investment.
#
# Made for myself to see how net worth I can attain at certain ages
# based on a variety of factors, but feel free in input your own numbers
# into the simulation if you come across this on my Github!
#
# Most estimates are highly conservative.
#

# Estimated 80000-85000 (conservatively) as a starting aerospace engineer in California
income = int(input("Enter your starting yearly income: ")) 

# Whatever investments/net worth you already have coming out of college (only a few dozen IVV and VNQ shares for now)
net_worth = int(input("Enter your starting net worth: "))

# 25-40% (before taxes) is usually a good range when income isn't insanely high yet
percent_saved = int(input("Enter the initial percentage of your gross income saved per year (a number 0-100): "))/100

# I'll start making an income at age 21 (bachelors only) or 23 (with a masters)
starting_age = int(input("Enter the age at which you begin investing: "))

# An age at which you'd arbitrarily like to stop the simulation
max_age = int(input("Enter the age at which you would like to limit analysis: "))


for age in range(starting_age,max_age+1):
    # Display net worth, income, and percentage of income saved at each age
    print("At " + str(age) + " years old, your net worth is $" + str(net_worth))
    print("At " + str(age) + " years old, your income is $" + str(income))
    print("At " + str(age) + " years old, you're saving " + str(percent_saved*100) + "% of your income")
    
    # Assume an average annual 9% S&P 500 return (Dividends reinvested)
    net_worth = 1.09*net_worth + percent_saved*income # Calculate new net worth
    
    # Assume an average annual raise of 4.6% (as a really good employee!)
    income *= 1.046 # Calculate new income
    
    # Save more of income as living expenses become a smaller part of income
    percent_saved *= 1.01 # Calculate new % of income saved
    # ^could've made a seperate function to make this approach a realistic limit
    
    