# An Analysis of Pyber Fare Data by City Type

## Overview and Purpose of Project
The analyst was tasked with conducting a python analysis that analyzed fare data by city type (urban, suburban, rural) for Omar, a colleague at Pyber, a ride share company.  Omar, and the analyst have been assigned this task by V. Isualize, the CEO and data analytics legend.  through importing python libraries such as pandas and matplotlib, the analyst was able to create a summary dataframe from a csv file, and turn that dataframe into a multiple-line chart illustrating total fares for each city type. 

## Analysis and Results

As noted previously, the python analysis that was conducted gathered ride share data for (3) city types urban, suburban, and rural.  The data was read into a jupyter notebook file from a CSV file using the follow code:

     # Add Matplotlib inline magic command
     %matplotlib inline
     # Dependencies and Setup
     import matplotlib.pyplot as plt
     import pandas as pd

     #File to Load (Remember to change these)
     city_data_to_load = "Resources/city_data.csv"
     ride_data_to_load = "Resources/ride_data.csv"

     # Read the City and Ride Data
     city_data_df = pd.read_csv(city_data_to_load)
     ride_data_df = pd.read_csv(ride_data_to_load)

Once the data was successfully read, the analyst used merged the city and ride dataframes, and used .groupby and various summary statistic methods (.mean(), .count(), .sum(), etc...) to gather/calculate totals and averages for the number of rides, drivers, and amount of fares for each city type.  The resulting data was then formatted and turned into a summary dataframe that showed the results in a format that made it easy to compare the statics across the types of cities.  The summary dataframe is shown below:

![Summary_DataFrame.png](https://github.com/hillmanj1995/PyBer_Analysis/blob/main/Resources/Summary_DataFrame.png)

While a summary dataframe is helpful to compare and contrast the various data aggregations, a visualization can be more effective at communicating data over a period of time to the client.  To create the visualization, the analyst retured to the original merged dataframe that they had used to create the summary dataframe.  Using that dataframe, they gathered and filtered the ride share data to create dataframe that showed the sum of the fares per week over a four month period (2019-01-01 to 2019-04-29).  The resulting dataframe is shown below:

![Fares_per_week.png](https://github.com/hillmanj1995/PyBer_Analysis/blob/main/Resources/Fares_per_week.png)

Using that dataframe, the analyst used the object oriented interface method to create a multiple-line chart showing the fare data over the four month period.  They formatted the plot using commands such as .set_title, .set_xlabel, and plt.legend, to provide necessary information for the client to easy understand the differences in the data they are reviewing.  The code used to format the plot, and the multiple-line plot are shown below:

    # 8. Using the object-oriented interface method, plot the resample DataFrame  using the df.plot() function. 

    # Import the style from Matplotlib.
    from matplotlib import style
    # Use the graph style fivethirtyeight.
    style.use('fivethirtyeight')

    weekly_fares = weekly_fares_df.plot(figsize = (20,6))
    weekly_fares.set_title("Weekly Fares")
    weekly_fares.set_xlabel("Date")
    weekly_fares.set_ylabel("Fare ($USD)")

    lgnd = plt.legend(fontsize='12',mode='Expanded', loc="best", title="City Types")
    lgnd.get_title().set_fontsize(12)

    plt.savefig('analysis/PyBer_fare_summary')

![PyBer_fare_summary.png](https://github.com/hillmanj1995/PyBer_Analysis/blob/main/Resources/PyBer_fare_summary.png)

## Summary
The data visualization shows that the as the areas get increasingly more urban, there is a higher yield in fares.  This is likely due to an increase in population and demand.  By reviewing this plot and the summary dataframe, Omar and the analyst can recommend the following to V. Isualize: 1.) The rural cities only have a total of 78 drivers, which is exponentially lower than that of suburban and urban cities.  Pyber should increase the number of drivers in rural areas to keep up with demand/make Pyber more available.  2.) In order to maximize profits, Pyber can increase fares in the urban areas.  These areas see roughly 2.6x the number of rides than the suburban areas, so demand is high.  If the average fare per ride increased by 25% (to $30.67), Pyber would return a higher profit than what is shown in the summary dataframe (from $39,854.38 to $49,838.80 (assuming demand remains the same)), unless demand dips by roughly 20% (to 1300 rides), which is unlikely. 3.)  An analysis should be conducted filtering on travel time.  The average fare per ride and per driver are higher in the rural cities than suburban and urban.  By looking at travel time vs. fares, it'll be easier to visualize why some of the fares are higher than the others. 
