# Jim Finnegan
[finnegan.jim@yahoo.com](mailto:finnegan.jim@yahoo.com?subject=GitHub%20Portfolio) | [LinkedIn](https://www.linkedin.com/in/james-m-finnegan/)

#### I am passionate about statistics and data science, particularly their applications to finance, earth science, and engineering. I built on my introductory undergraduate computer science courses with self-teaching and independent projects that are showcased in this portfolio. I implement computational skills and numerical methods using Python, MATLAB, and ArcGIS. I have taught myself statistical and computer skills including data scraping, object oriented programming, data anlysis, visualization, and machine learning. I am always working on building new skills and tackling exciting new projects.

<br/><br/><br/>

# Data Scraping and Analysis - Python
## [ESPN FPI Model](https://github.com/jmfinnegan12/FPI-Scrape)
#### Independent Project
- built a web scraper for two separate pages on ESPN.com
- calculated implied winning probabilities for football games based on data
- analyzed sports betting markets with implied probabilities to suggest statistically favorable bets


<details><summary>View some sample code</summary>
<p>
  
```python
# up to date FPI function
# returns pandas dataframe with current FPI table

def getFPI():
    url = 'https://www.espn.com/nfl/fpi'
    r = requests.get(url)
    html = r.text
    
    # ESPN splits the FPI table into two sides
    
    # put the left table (team names) into a pandas dataframe    
    soup = BeautifulSoup(html)
    table1 = soup.find('table', {"class": "Table Table--align-right Table--fixed Table--fixed-left"})
    rows = table1.find_all('tr')
    teams_data = []
    for row in rows[2:]:
        cols = row.find_all('td')
        cols = [element.text.strip() for element in cols]
        teams_data.append([element for element in cols if element])   

    teams_df = pd.DataFrame(teams_data)
    
    # put the right side table (FPI and other stats) into a pandas dataframe
    table2 = soup.find('table', {"class": "Table Table--align-right"})
    rows = table2.find_all('tr')
    stats_data = []
    for row in rows[2:]:
        cols = row.find_all('td')
        cols = [element.text.strip() for element in cols]
        stats_data.append([element for element in cols if element])   

    stats_df = pd.DataFrame(stats_data)
    
    # combine into one dataframe and update headings
    df = pd.merge(teams_df, stats_df, left_index=True, right_index=True)
    headers = {'0_x': 'TEAM', 
               '0_y': 'W-L', 
               1 : 'FPI', 
               2: 'RK', 
               3: 'TRND', 
               4: 'OFF', 
               5: 'DEF', 
               6: 'ST', 
               7: 'SOS', 
               8: 'REM_SOS', 
               9: 'AVG_WP'}
    df = df.rename(index=str,columns=headers)
    return df
```
</p>
</details>
<br/>

# Object Oriented Programming, Statistical Simulation - Python
## [Monte Carlo Simulation](https://github.com/jmfinnegan12/Monte-Carlo)
#### Independent Project
- Simulated a roulette spin using object oriented programming
- Ran statistical simulation on numerical trials
- Visualized results  
![](https://github.com/jmfinnegan12/Monte-Carlo/blob/main/Photos/GamblersFallacy%20Dist.PNG)

# Numerical Methods - Python
## [1-D Solute Transport Model](https://github.com/jmfinnegan12/1Dtransport)
#### Groundwater Modeling, Tufts University
- built models for 1-D solute transport in porous medium using python
- Crank-Nicholson centered finite difference scheme
- Galerkin finite element method 
- Compared the models to the analytical solution for various initial conditions and parameters
![](/images/comparison_D_1_t400.png)

<br/>

# Text Recognition and Processing - Python
#### Independent projects to improve productivity at work -- [full repo](https://github.com/jmfinnegan12/pdf)
## [PDF Table Reader](https://github.com/jmfinnegan12/pdf/blob/main/TableReader_finalized.ipynb)
- built a program to scrape tables from PDF documents
- converts tables to pandas dataframe, excel, or csv
- saved hours preventing the need to manually transcribe tables--possibility for future expansion and industry-disrupting results


## [PDF Highlighter](https://github.com/jmfinnegan12/pdf/blob/main/PDF%20Highlight.ipynb)
- built a program to highlight text on a PDF with over 3,000 labels
- provides accurate, up to date production tracking for two projects, each worth $1.8 million

<br/>

# GIS - ArcMAP
## [Avalanche Risk Analysis](https://github.com/jmfinnegan12/avalanche)
#### Geological Applications of GIS, Tufts University
- Reached the final round of 20 out of over 250 posters in Tufts University GIS poster session
- Synthesized several publically available datasets
- Created a comprehensive risk analysis using GIS methods including raster analysis, reclassification, and intersection
![](/images/risk_map.PNG)

<br/>

# Numerical Methods - MATLAB
## [Fluid Flow Around an Airfoil Simulation](https://github.com/jmfinnegan12/fluid-flow)
#### Numerical Methods, Tufts University
This program models the flow of a fluid with a constant horizontal velocity around a symmetrical airfoil using MATLAB. The script takes a streamline matrix defined in Microsoft Excel and calculates the horizontal velocity, vertical velocity, and total velocity of the fluid using discrete and regression methods. It also uses plots to display streamlines visually.
![](/images/Streamlines.PNG)
![](/images/Surface%20Fit%20Plots.PNG)

