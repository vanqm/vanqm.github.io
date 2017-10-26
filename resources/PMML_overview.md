## What is PMML?
The Predictive Model Markup Language (PMML) developed by the Data Mining Group is a standardized XML-based representation of mining models to be used and shared across languages or tools. The standardized definition allows a classification model trained with R to be used with Storm for example.

## Step-by-step How to apply ML into factory by using PMML?
- **Step 1**: Using Python/R/Weka/Knime... to develop the ML model
- **Step 2**: Exporting the model into PMML file
  - [Python] https://github.com/jpmml/sklearn2pmml
- **Step 3**: Using PMML file to predict
  - Case 1: Appliction
    - [JPMML] http://henning.kropponline.de/2015/09/06/jpmml-example-random-forest/
  - Case 2: Web service with OpensSoring
    - [R] https://www.r-bloggers.com/predictive-modeling-using-r-and-the-openscoring-engine-a-pmml-approach/
    - [R] https://journal.r-project.org/archive/2009-1/RJournal_2009-1_Guazzelli+et+al.pdf
