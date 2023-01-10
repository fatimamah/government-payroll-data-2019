# Visualization of U.S. &amp; State Government: Payroll Data for March 2019

Info 3300: Data Driven Web Visalizations–Project 1    

Group Members: Fatima Mahmoud (fam76), Ayesha Kemal (ak2235), and Zoe Gonzalez-Llorens (zg226)

To run web server, use `python -m http.server` for python 3

## Final Visualization

![final bar graph](https://user-images.githubusercontent.com/58915939/211435863-73cffea6-313f-4ec9-a0bd-26ea3ddd761d.png)

![final choropleth](https://user-images.githubusercontent.com/58915939/211435799-8d491615-8a56-4458-b480-52d6b705cecb.png)


https://user-images.githubusercontent.com/58915939/211435480-59480408-e670-44c0-9ba4-39bd0320b215.mp4

## Data

### Data Source

- Our group obtained data from the [March 2019 Census ASPEP Dataset](https://www.census.gov/content/census/en/data/datasets/2019/econ/apes/annual-apes.html) and more closely examined the State Government Employment & Payroll Data Excel file

### Data Cleaning

- Changed state abbreviations to states’ full name and took out all the columns except for state, government function, and total march payroll (whole dollars). 
- Changed from excel file to csv by saving at as csv (comma delimited) then used [this online converter](https://www.convertcsv.com/csv-to-json.htm) to convert it to json file.
- Converted payroll from strings to numbers.  

  **For Choropleth:**
  - Filtered out the US general--not state specific-- data.
  - Filtered out data that had 0 for payroll.
  - Filtered out the Total - All Government Employment Functions data
  - Filtered out data that had “Total” in the Government Function (ex: “Police Protection Total”)
  - Filtered out all data with Higher Education in the Government Function  
  
  **For Bar Graph:**
  - Add a column “Percent” that was each payroll divided by the total payroll.
  - Filtered out the Total - All Government Employment Functions data
  - Filtered out data that had “Total” in the Government Function (ex: “Police Protection Total”)
  - Filtered out states that were not US (only kept overall/general US data).
  
### Data Variables

- State: State name. A string.
- Government Function: The government function/a category of government work. A string.
- Total March Payroll (whole dollars): The full time and part time payroll for March 2019. A number.

### Additional Data

- d3.geoAlbersUsa() shape map
- Professor Rzeszotarski’s Dataset: us-state-names.tsv
- Professor Rzeszotarski’s Dataset: Us1.json 

## Design Rationale

Our group first chose to display the bar graph showing in the United States how out of the total funds varied. More specifically, our group wanted to show the disparity between Education - Higher Education Instructional/Education - Higher Education Other and the remaining entries. For this section, our group added a “Percent” entry which took the Total March Payroll for a specific category, such as Hospitals, and divided it by the Total March Payroll amount, which was $24,709,368,217. For each entry, we appended the data onto the bar chart.

For our x-axis, we placed the name of the Government Function. One of the problems we encountered was that the titles for many of the Government Functions were extremely long and did not fit on the traditional x axis label without overlapping. Because of this, we opted to use a rotated x-axis label so that the data would fit on the svg and be readable for the users. For our y-axis, we utilized percentages, from 0% to 100%, to show the users, out of the whole Total March Payroll what percent each specific Government Function took up in the entire country. One issue we have with using 0% to 100% is that the data is more compressed as most of the percentages are between 0% and 30%. Due to this issue, we decided it would be best to have the domain of the bar chart to be between 0% and 50% so that the data is presented in a more readable format. We did not use gridlines for the x-axis as it was unnecessary given we were using a bar chart method to display our data. For our color, we elected to use “steelblue” for the bar chart lines as the users only need to distinguish the height of the bars rather than colors. Our group utilized a linear scale for our bar chart because the data is linear.

For our group visualization, we wanted to display the highest total payroll data in comparison with other states within the United States. To do this, we used the d3 json file us1.json which Professor Rzeszotarski utilized in his March 24th lecture. Our rationale was that we (I) wanted to see a state’s highest payroll data and (II) if states sharing borders also shared the same highest payroll. We used the d3.geoAlbersUsa() because the position was consistent with what users would expect for a map of the United States. If we had used another projection, such as the d3.geoMercator() projection, the map would have been extremely stretched out and it would have made interpreting the colors on the U.S. map hard.  

When our group was able to begin our second visualization, the first problem we encountered was when we were finally able to see the choropleth of the distribution of highest payrolls per state, most, if not all, of the states had their highest payroll in Higher Education. There was no diversity in the choropleth data, almost everything was colored in for Higher Education. In recognizing this problem, our group decided to omit the payroll data for Higher Education. In doing this, we were able to clearly see the differences in how different state’s payrolls were allocated. 

Some categories our group chose to emit included any data regarding the United States as a whole. Since the choropleth visualization on needed data for states, there was no reason to include the total countries data. In addition, we removed any data regarding Higher Education as those numbers were disproportionately larger than the rest of the data as mentioned above and every state would have Higher Education as the government function with the highest payroll. We knew that Higher Education is disproportionately larger than the other government functions from the bar graph, and wanted to see if any patterns emerged or if there was anything interesting when we  took out theHigher Education data.We also removed data from “All other and unallocable” as it was not specific. Lastly, we removed data that included Totals such as “Police Protection Total” as the data skewed our results because there were subcategories for each state that painted a more accurate representation of payroll data such as “Police Protection - Persons with Power of Arrest.” 

For our color scale, we decided to use a nominal color scale and categorical palette, d3.schemeSet1, as there is no specific order for the scale. D3.schemeSet1 is an array consisting of nine categorical colors. Displaying unordered hue works as we are only displaying eight color hues. With using a categorical palette, we were certain that the colors would be easily recognizable and distinguishable to the users. Our group tested the scale on an online color blindness image testing tool ([Coblis — Color Blindness Simulator – Colblindor] (https://www.color-blindness.com/coblis-color-blindness-simulator/)) in order to ensure that the scale would be accessible for users with color blindness. For most conditions, we could still distinguish various hues from each other with only one case of two close values in an Deuteranopia Dichromatic view. 

## The Story

Our motivation for the first visualization was that our group wanted to see the United States’, as a whole, payroll data. Although we were planning on looking at the states in the choropleth map, we thought that a good place to begin our analysis would be looking at the total data. 
Our motivation for the second visualization  was that our group wanted to analyze how each state in the United States payroll data differed from another state. We wanted to find if there were any common trends and wanted to visually see this representation looking at the map of the United States. As we began entering data onto the choropleth map, we saw certain data such as Totals and Higher Education was skewing our results. In order to paint a better picture, we decided to omit this data as it was not adding anything to our final analysis.

From the bar graph, we can see that higher education is significantly larger than all of the other government functions. So overall, the United States allocates the most money in payroll to higher education (to both instructors and other workers). Elementary and secondary education however have some of the lowest payrolls. The graph really shows the discrepancy between the different levels of education.  That was surprising to us because we expected police protection to be highest by a lot. Our reasoning was that there are police in every town/city so there’s more workers in that category and police usually have unions and can negotiate for better salaries, while many people in other industries are not unionized. Police also get a lot of funding and we thought that would reflect in the payroll. 

Many government functions had payrolls that accounted for close to 0% of the total government functions payroll. This includes fire protection, solid waste management, sewerage, water supply, electric power, gas supply, libraries, and state liquor stores. Fire protection is something we knew would be 0 or just really low because most fire departments are volunteer based. However, necessary functions such as electric power or sewerage was surprising because they are so needed and used.After some research, we’ve learned that a lot of those government functions/departments outsource their work to private companies so the government is not paying the workers ([Article](https://www.cato.org/tax-budget-bulletin/privatizing-federal-electricity-infrastructure), [Wikipedia](https://en.wikipedia.org/wiki/Water_privatization_in_the_United_States)).

From the choropleth, we can see the government functions, excluding higher education, that have the highest payroll in each state. The choropleth is mainly red and green, which indicates that the highest government functions payrolls are hospitals and corrections. We expected the highest to be really different for every state, but with this map (and even if we included higher ed,) the states seem to have similar payrolls, which means that they pay ppl in the same work somewhat similarly when compared to other work in that state. 

If we were to view the payroll as how important that government function is to our society or how much we value that function, these two graphs tell us that higher education, followed by hospitals and corrections are the most important and valued functions or needs. 

Out of the 50 states, 18 states, 36%, had Hospitals as the highest government function excluding higher education and 16 states, 32%, had Corrections as the highest government function. These numbers shed light as to functions certain state governments value. These two functions, Hospitals and Corrections, perhaps reflect the values not only of a state but of our nation as well. It would be interesting to see if the states that had Hospitals as their highest, have more hospitals than other states, and if the states that had Corrections, have more prisons or a higher incarceration rate than other states. 

Lastly, our group wanted to convey that while many states shared the same highest government function, no states’ payroll data is the same. Each state has its own values that reflect their population and allocate funds accordingly. Our goal was to show user’s how their states compare to other states and whether a state’s payroll is similar or different to the rest of the country. 

## Team Contributions

Fatima: Wrote report (data and part of story) and coded.
Ayesha: Wrote report, coded, and looked at online resources to use for project
Zoe: Wrote report, coded, and attended office hours to ask the group’s questions 

We all coded and communicated the entire time through text, so all of the code was collaborative (ex: one person would make the graph scales and axes, someone else make the rectangles/bars, and the other debug to see why the data isn’t loading) . We spent a total of about 16 hours coding the project and about 2 hours writing the report. Writing the function that found the government function with the highest payroll for each state and updating statesCount took the longest (about 5 hours). 


