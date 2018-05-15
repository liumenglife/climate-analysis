# climate-analysis

Dataset used: https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data/data
How to run program:
- Download the dataset and save it in a folder called data in your directory.
- Install numpy, pandas, scikit-learn, and matplotlib for Python3. 
- Run program using Python3 .
- The program will take a few minutes to read and sort the dataset.
- Create a graph for city, country, or the world using the corresponding make_graph function. (Might take a few minutes.)
  For example to make a graph for Los Angeles, run make_graph_city("Los Angeles", "United States").
  You can also make a graph for entire countries. Example: make_graph_country("China)
*You can freely explore the dataset yourself in your console. The pandas dataframe is called "data".

## Project Details and Goals
For the following analysis I used the following dataset provided by Kaggle:

My goal for this project is simple: I want to illustrate that climate change is causing the earth's overall temperature to slowly rise over time. According to the Intergovernmental Panel on Climate Change(IPCC), climate change is a persistent trend that occurs over a large period of time. Natural events such as El Nino cause short, temporal changes in average temperature so they are not classified as climate change. https://www.ipcc.ch/publications_and_data/ar4/wg1/en/ch9s9-1.html 

To accomplish my goal, I will perform a regression analysis to show that the average temperature of the earth is rising over time. 

I will write a collection of functions to prepare the climate data for analysis. The dataset is a csv file that contains the recorded average surface temperature of most major cities in the world since the 1750s. It comes from a reputable source called Berkeley Earth which compiles climate data from 16 different sources. The column values are all fairly straightforward. They are the following: AverageTemperature, AverageTemperatureUncertainty, City, Country, Latitude, and Longitude. AverageTemperatureUncertainity is the amount the recorded Average Temperature for that day may be off by. This program, I generalized my program so that it can produce a valid graph for any city or country that is given that exists in our dataset. It can also produce a graph for the entire world in general.

## Data Preparation
At the start of my program I sort all values by datetime which is costly but only needs to be performed once. Since it is necessary for my program to be efficient, I might as well do it at the beginning of the program to avoid repeatedly sorting the dataset every time you call a function.

I want to manipulate my data such that I have the average temperature for every year in a given location, starting from the first year where data is consistently recorded (no skipped year). The reason for avoid gaps in data is to properly fit our temperature values into our regression model is that any gaps will cause the regression to skew too much that it becomes unreliable. So when we are searching and cleaning our data, I need to make sure that there are no missing values in my data and also for no missing years in my value. Finding and removing missing values in pandas is trivial. However, finding gaps between year may require manual scanning so I wrote a small function to recognize a gap and return a dataset without gaps. After I prepare all the data I need, I simply add up mean temperature values and calculate the mean of average temperature for each year. To make my data visualization more honest, I also calculated the mean of AverageTemperatureUncertainty values in the same way so that I can also plot them on the graph to show the possible values the mean might be off by. After calculating the means, I have all the data I need to use more the data visualization.

## Data and Regression Analysis
Now, I can plot my values into a graph and see that the output is. For the values in my data, the y-axis represents the temperature while the x-axis represents the year. There are always going to be occasional dips and shaky lines in our graph but this is normal as these only represent short trends in climate and not change over a large period of time as mentioned earlier in this analysis. Depending on the city/country chosen, it might be easier or harder to see how the graph is slowly rising, but for all graphs, you can see that the line graph is slowly increasing. However, we can communicate this trend much more clearer with a simple regression. 

A regression analysis demonstrates the relationship between a set of independent variables on a dependent variable. Using our real-world knowledge, we know that time will always be constant and moving forward irregardless of anything that occurs in our world. We know that temperature can be influenced by a wide variety of variables including time (e.g. The temperature is lower at night when the sun is down, and higher when the sun is above us). Therefore, we can perform regression using these two as our set of independent and dependent variables. The regression we will perform is a simple linear regression because our independent variable(temperature) is continuous variable (it can be any possible value). The data we have is already sufficient enough to fit into a linear regression model as year is a representation of time.  A linear regression model statistically predicts possible y-values(temperature in our data) over time by recognizing patterns in our dataset. Of course, the predict values in our model will not be completely accurate because temperature is affected by numerous variables. However, it will tell us the predicted behavior of temperature over the course of time.

By plotting our predicted y-values onto the same graph, we can more clearly see the behavior of temperature over time. Since our regression line has a positive slope, this suggests that as time passes, temperature also rises. The predicted values also suggest that the Earth’s average temperature has risen by about 1 degree celsius since the 1750s. This strongly verifies the existence of climate change.

## Conclusion
We have clearly illustrated that the world's temperature is rising around the world using clear and easy-to-understand visuals. If you plot multiple cities and countries and compare their climate data, you will see that the severity of the warming will vary greatly. This is due to other factors such as geography (e.g. how close to a body of water it is). But we can conclude that there is general trend of rising temperatures over time, regardless of location.

## Possible Future Work and Improvements
Possible ideas and methods to improve and build upon this project might be to collect additional data such as ocean temperature, humidity, ect. It might be interesting to see how the maximum and minimum temperatures are changing. Maybe hotter days are getting hotter or more frequent. Additional data also gives us additional variables to be able to perform more complicated multivariate regressions and graphs. There are also a number of other ways we can look at the data we already have such as looking average temperature of the seasons over the year which might also be another way of looking at extreme temperature.

Overall, I had a lot of fun learning how to look at data for meaningful research. 

All code was written by me. Dataset provided by kaggle.
