# I-Grade (inteligent grade prediction system)
Grade prediction system based on trend of the recorded data in database. User select its habit then get the grade closest to the final result.

# Requirments and prepration
This project is based on the following technology:
* Data
  + Pandas
  + Numpy
  
* Model
  + Sikit-learn
  
* Web side
  + Flask
  + Bootstrap

* visualisation
  + Chartjs

# App Structure
we can seprate this project (Flask framework) to several main part with different functionality.

App (I-grade):
  + static (folder)
    + css (folder)
      + bootstrap
    + datasets (folder)
      + dataset_main.csv // main dataset for making model
    + images (folder)
      + Logo.png 
      + ki.jpg
    + javascript (folder)
      + viz.js // main javascript file for making charts
  + template (folder)
    + index.html
    + prediction.html // page of showing the prediciton result
    + question_form.html // the form for getting user input
  + Convertor.py
  + Model_classification.py // clasifier model
  + plot.py // preparing data to use for plotting
  + server.py // application server backend part
  

# Step 1
### Data prepration
for making our model and use it for the prediction we need to first prepare the data for process.
