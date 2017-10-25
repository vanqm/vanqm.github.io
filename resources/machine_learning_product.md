# ML Product

## Building a Production Machine Learning Infrastructure
Ref: https://machinelearningmastery.com/building-a-production-machine-learning-infrastructure/

Josh Wills gave a talk on what it takes to build production machine learning infrastructure in a talk titled "[From the lab to the factory: Building a Production Machine Learning Infrastructure](https://www.youtube.com/watch?v=IgfRdDjLxe0)".

Josh says that his current passion is **feature engineering**, that is the dark art of industrial machine learning.

**Industrial Machine Learning Frameworks**
- [Architecting a Machine Learning System for Risk](https://medium.com/airbnb-engineering/architecting-a-machine-learning-system-for-risk-941abbba5a60)
  - [Openscoring](https://github.com/andykram/openscoring)
  - Python and Scikit-learn library
  - Java PMML: Java Predictive Model Markup Language is an XML markup language that encodes several common types of machine learning models.
  - [PMLL](https://github.com/vanqm/pmll): **P**ython **M**achine **L**earning **L**ibrary

## How to Use Machine Learning Results?
Ref: https://machinelearningmastery.com/how-to-use-machine-learning-results/

Depending on the type of problem you are trying to solve, the presentation of results will be very different. There are two main facets to making use of the results of your machine learning endeavor:
- Report the results
  - **Context** (Why): Define the environment in which the problem exists and set up the motivation for the research question.
  - **Problem** (Question): Concisely describe the problem as a question that you went out and answered.
  - **Solution** (Answer): Concisely describe the solution as an answer to the question you posed in the previous section. Be specific.
  - **Findings**: Bulleted lists of discoveries you made along the way that interest the audience. They may be discoveries in the data, methods that did or did not work or the model performance benefits you achieved along your journey.
  - **Limitations**: Consider where the model does not work or questions that the model does not answer. Do not shy away from these questions, defining where the model excels is more trusted if you can define where it does not excel.
  - **Conclusions** (Why+Question+Answer): Revisit the why, research question and the answer you discovered in a tight little package that is easy to remember and repeat for yourself and others.
- Operationalize the system
  - Algorithm Implementation
  - Model Tests
  - Tracking

## How to Deploy Your Predictive Model To Production
Ref: https://machinelearningmastery.com/deploy-machine-learning-model-to-production/
  
#### I Have a Model. Now What?
So you have been through a systematic process and created a reliable and accurate model that can make predictions for your problem.

You want to use this model somehow.
- Maybe you want to create a standalone program that can make ad hoc predictions.
- Maybe you want to incorporate the model into your existing software.

Let’s assume that your software is modest. You are not looking for Google-sized scale deployment. Maybe it’s just for you, maybe just a client or maybe for a few workstations.

#### 5 Model Deployment Best Practices
1. Specify Performance Requirements
2. Separate Prediction Algorithm From Model Coefficients 
    - 2a. Select or Implement The Prediction Algorithm 
    - 2b. Serialize Your Model Coefficients
3. Develop Automated Tests For Your Model
4. Develop Back-Testing and Now-Testing Infrastructure
5. Challenge Then Trial Model Updates
  
## [Quora] What is the easiest way to deploy a machine learning model (say a regression) for production?
Ref: https://www.quora.com/What-is-the-easiest-way-to-deploy-a-machine-learning-model-say-a-regression-for-production

It include:
- Wsgi and NginX
- Flask main application file
  - [Simple Flask Example | Authomatic ](http://peterhudec.github.io/authomatic/examples/flask-simple.html)
  - [Quickstart - Flask Documentation (0.10) ](http://flask.pocoo.org/docs/0.10/quickstart/)
- Microsoft Azure
  - [Step 5: Deploy the Machine Learning web service](https://docs.microsoft.com/en-us/azure/machine-learning/studio/walkthrough-5-publish-web-service)
  - [Deploy a Machine Learning web service](https://docs.microsoft.com/en-us/azure/machine-learning/machine-learning-publish-a-machine-learning-web-service)
- Flask and Docker: https://blog.solutotlv.com/deployed-scikit-learn-model-flask-docker/?utm_medium=What-is-the-easiest-way-to-deploy-a-machine-learning-model-say-a-regression-for-production&utm_source=quora
