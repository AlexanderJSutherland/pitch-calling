# Umpiring in the Age of Techonology
# A Study of Pitch Calling by MLB Umpires
## *Alexander J. Sutherland*

### Overview  
In 2024, the pitch calling abilities of home plate umpires are under more scrutiny than ever: entities like Ump Scorecards publish summaries of home plate umpire performance for every Major League Baseball (MLB) game on social media (Ump Scorecards, 2024) and all AAA-level games in Minor League Baseball (MiLB) used the automated ball-strike (ABS) challenge system as of June 25th (Harrigan, 2024). Given the importance of correct calls to both game outcomes and fans – as well as the looming possibility of an ABS system in MLB games – we investigate both: 
+ 1) the efficacy of machine learning models to predict umpires’ ball/strike calls, and
+ 2) what features most impact calling balls and strikes (outside of pitch location).


### Project Stakeholders
MLB, MiLB, Professional baseball organizations, Professional baseball umpires, Professional baseball players, Baseball fans.

### Methods  
Regarding task 1), we used both logistic regression and linear support vector classifier models trained on pitch location data and umpire information with 10-fold cross validation and hyperparameter tuning via grid search. These models were compared against coin-flip baseline models, where the odds of a pitch being called a strike matched the percentage of strikes present in the data frame.  
  
For task 2), we provide visualizations of umpires’ correct call percentages across a much wider class of features that are not location-based. We then perform feature selection using both forward selection and L^1 regularization to determine which features are most important in determining when an umpire will make a correct call.

### Key Performance Indicators (KPIs)  
For all our models, we prioritize model accuracy. We additionally track F1-score and PR-AUC as secondary metrics.

### Files and Data

#### Jupyter Notebooks (.IPYNB)
The main files for this project are Jupyter notebooks, of which there are five:
+ `Umpiring in the Age of Technology - A Study of Pitch Calling by MLB Umpires - Executed Notebook` is the primary file with all cells executed and saved.
+ `Umpiring in the Age of Technology - A Study of Pitch Calling by MLB Umpires - Unexecuted Notebook` is the primary file with no cells executed.
+ `2023 MLB Pitch Data - Month by Month Queries using Pybaseball` uses `Pybaseball` to directly query *Baseball Savant*. Running this notebook accesses the original data and exports the data locally as CSVs. This notebook is included for completeness, but does not need to be ran, as the data is included with this project.
+ `2023 MLB Pitch Data - Merging, Cleaning, and Processing` imports the data that was exported from *Baseball Savant*, imports the umpire data scraped from *Baseball Reference* (see below), and does all of the necessary steps with the data before importing into the main project.
+ `2023 MLB Umpire Data` scrapes umpire information from *Baseball Reference* using `BeautifulSoup` and exports the data locally as CSVs.  
  
The data collection and processing is discussed further in `Appendix A` of `Umpiring in the Age of Technology - A Study of Pitch Calling by MLB Umpires - Executed Notebook`.

#### Microsoft Word Documents (.DOC)
The `Executive Summary` is essentially a shorter version of this README file detailing the most important parts of this project.

#### Adobe Acrobat Documents (.PDF)
For greater accessibility, we include PDF versions of the notebook `Umpiring in the Age of Technology - A Study of Pitch Calling by MLB Umpires - Executed Notebook` and the Word document `Executive Summary`.

#### Comma Separated Values Files (.CSV)

##### Data Collection Imports and Exports

###### `???_umpire`
CSV files titled in the style `???_umpire` contain umpire information exported from the `2023 MLB Umpire Data` notebook.

###### `month?`
CSV files titled in the style `month?` contain MLB pitch data exported from the `2023 MLB Pitch Data - Month by Month Queries using Pybaseball` notebook.

###### Others
+ `large_model_data` and `small_model_data` are the final, processed exports from `2023 MLB Pitch Data - Merging, Cleaning, and Processing` that are imported into the primary notebooks.
+ `missing_umpires` is data exported from `2023 MLB Pitch Data - Merging, Cleaning, and Processing` and imported into `2023 MLB Umpire Data` for scraping information about doubleheader games; `missing_umpires_return` is exported from `2023 MLB Umpire Data` and imported into `2023 MLB Pitch Data - Merging, Cleaning, and Processing` containing the required data about doubleheader games.
+ `umpires` is the primary file exported by `2023 MLB Umpire Data` containing umpire information that is then imported into `2023 MLB Pitch Data - Merging, Cleaning, and Processing`.

##### Modeling Imports and Exports
When modeling, we use two data frames (`horizontal` and `vertical`), include or ignore the `umpire` feature, and use a logistic regression or a support vector machine model. For each of these choices, we tune various hyperparameters and save the results as a CSV with a corresponding name.  
  
For example, `vert_no_ump_svm_grid_results` contains the results of tuning hyperparameters for an SVM-based model trained on the `vertical` data frame and does not use the `umpire` feature.  
  
#### Video Files (.MP4)
There are eight video files in this project, all of which are called in the main notebooks.  
  
The files `heart_video`, `shadow_video`, `chase_video`, and `waste_video` are all video examples of pitches in the four different regions of the strike zone (heart, shadow, chase, and waste regions).  
  
The files `baker_video_1`, `baker_video_2`, `baker_video_3`, and `tumpane_video_1` are all videos of the four outlier MLB pitches from 2023 that crossed the plate in the waste region of the zone but were called incorrectly.

#### Picture files (.PNG)
The file `heart_shadow_chase_waste` gives a visual description of these four regions of the strike zone and the file `statcast-gameday-zones` gives a similar visual description of the Statcast gameday regions of the strike zone.

### Conclusions and Future Work
Each of our models – trained on real umpire calls – consistently outperformed the actual umpires, with gains as large as 2.95% (with umpire correctly calling 91.76% of pitches and our model predicting 94.72% of pitches correctly). Additionally, we found that the most important (non-location-based) factors for predicting correct umpire calls were the pitch count, height of the regulation strike zone, effective pitch speed, and vertical pitch movement. Future work should consider a longitudinal study of non-location-based factors on predicting correct umpire calls, as well as a thorough study of the new ABS system in MiLB.

### References
+ Harrigan, T. (2024, Jun 18). *Triple-A to employ challenge system over full ABS for rest of season.* Retrieved from MLB.com: https://www.mlb.com/news/triple-a-abs-challenge-system
+ LeDoux, J., & Schorr, M. (2024, Oct 03). *Pybaseball Github Repository Readme.* Retrieved from Pybaseball Github Repository: https://github.com/jldbc/pybaseball
+ MLB Advanced Media, LP. (2024, Oct 03). *Statcast Search.* Retrieved from Baseball Savant: https://baseballsavant.mlb.com/statcast_search
+ Sports Reference LLC. (2023, Oct 03). *Baseball Reference.* Retrieved from Baseball Reference: https://www.baseball-reference.com
+ Ump Scorecards. (2024, Oct 03). Retrieved from umpscorecards.com: https://umpscorecards.com/home/