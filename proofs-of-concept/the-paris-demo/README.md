---
description: >-
  This page demonstrates how you can leverage medical questionnaire data in
  MEDomics to draw insights.
icon: wpforms
---

# The PARIS Demo

{% hint style="warning" %}
The original data is not available. We have generated synthetic data using the [synthpop package](https://algorithmaudit.eu/technical-tools/sdg/), and this dataset will be released once we receive authorization from the PARIS team (expected in mid-2026).
{% endhint %}

### About the Dataset

Patient-Reported Indicators Surveys ([PARIS](https://ssaquebec.ca/projets/paris/)) is a combination of PROM (Patient-Reported Outcome Measures) data, which focuses on patient health status, and PREM (Patient-Reported Experience Measures) data, which captures the patient's experience with care. It represents a questionnaire completed by patients to provide a complementary view of healthcare quality, enabling organizations to track progress, identify areas for improvement, and personalize care. The data's columns/questions are illustrated in the table below.

### Goal

This POC aims to show how the PARIS data can be exploited using the MEDomics platform. We will explore how Superset can be used to both visualize and curate the data. Moreover, we will review several MEDomics modules to demonstrate the potential of each one in data processing and modelling, with the ultimate goal of **predicting** a pre-selected variable, in this case, **the patient's emotional distress**.&#x20;

{% hint style="info" %}
Initially, the PARIS dataset contained about 200 columns (questions), and to simplify this demo, we manually chose those we believe are linked to the clinical issue of mental distress.
{% endhint %}

<table><thead><tr><th>Column Name</th><th width="249">Question</th><th>Possbile Answers</th></tr></thead><tbody><tr><td>EnergeticVigorous2</td><td>I felt energetic and vigorous.</td><td><ol><li>All the time</li><li>Most of the time</li><li>More than half the time</li><li>Less than half the time</li><li>Occasionally</li><li>Never</li></ol></td></tr><tr><td>DailyLifeInterests2</td><td>My daily life has been filled with things that interest me.</td><td><ol><li>All the time</li><li>Most of the time</li><li>More than half the time</li><li>Less than half the time</li><li>Occasionally</li><li>Never</li></ol></td></tr><tr><td>SleepRested2</td><td>I woke up feeling rested and refreshed.</td><td><ol><li>All the time</li><li>Most of the time</li><li>More than half the time</li><li>Less than half the time</li><li>Occasionally</li><li>Never</li></ol></td></tr><tr><td>Fatigue7</td><td>Over the past 7 days, how would you rate your average level of fatigue?</td><td><ol><li>None</li><li>Mild</li><li>Moderate</li><li>Intense</li><li>Very intense</li></ol></td></tr><tr><td>ActivitiesPain7</td><td>Over the past 7 days, to what extent has pain interfered with your daily activities?</td><td><ol><li>Not at all</li><li>A little</li><li>Moderately</li><li>A lot</li><li>Extremely</li></ol></td></tr><tr><td>Pain7</td><td>Over the past 7 days, how would you rate your average pain level?</td><td><p> 0.  0- No pain</p><ol><li>1</li><li>2</li><li>3</li><li>4</li><li>5</li><li>6</li><li>7</li><li>8</li><li>9</li><li>10- The worst pain possible</li></ol></td></tr><tr><td>SocialRoles</td><td>Overall, how do you feel you are fulfilling your usual activities with others and your role in society (whether at home, at work, in your immediate environment, as well as your responsibilities as a parent, child, partner/spouse, employee, friend, etc.)?</td><td><ol><li>Excellent</li><li>Very good</li><li>Good</li><li>Mediocre</li><li>Poor</li></ol></td></tr><tr><td>PhysicalActivities</td><td>To what extent are you able to perform daily physical activities such as walking, climbing stairs, carrying shopping bags, or moving a chair?</td><td><ol><li>Completely</li><li>Almost completely</li><li>Moderately</li><li>A little</li><li>Not at all</li></ol></td></tr><tr><td>Age</td><td>Age</td><td><ol><li>44 years old or younger</li><li>Between 45 and 49 years old</li><li>Between 50 and 54 years old</li><li>Between 55 and 59 years old</li><li>Between 60 and 64 years old</li><li>Between 65 and 69 years old</li><li>Between 70 and 74 years old</li><li>Between 75 and 79 years old</li><li>Between 80 and 84 years old</li><li>85 years old or older</li></ol><p> 97. I prefer not to answer</p></td></tr><tr><td>Sex</td><td>Sex</td><td><ol><li>Female</li><li>Male</li><li>Non-binary</li><li>Other</li><li>I prefer not to answer</li></ol></td></tr><tr><td>NutritiousMeals12</td><td>Have enough money to buy nutritious meals?</td><td><ol><li>Always</li><li>Often</li><li>Sometimes</li><li>Rarely</li><li>Never</li></ol></td></tr><tr><td>RentMortgage12</td><td>Do you have enough money to pay your rent or mortgage?</td><td><ol><li>Always</li><li>Often</li><li>Sometimes</li><li>Rarely</li><li>Never</li></ol></td></tr><tr><td>MonthlyBills12</td><td>Do you have enough money to pay other monthly expenses, such as your electricity, heating, and phone bills?</td><td><ol><li>Always</li><li>Often</li><li>Sometimes</li><li>Rarely</li><li>Never</li></ol></td></tr><tr><td>DiscussionHealthcareProfessionals</td><td>Do you discuss with your healthcare professionals what is most important to you in managing your health and well-being?</td><td><ol><li>Not at all</li><li>To some extent</li><li>Most of the time</li><li>Always</li><li>Not applicable</li></ol></td></tr><tr><td>HealthcareInvolvement</td><td>Are you as involved as you would like to be in decisions about your care?</td><td><ol><li>Not at all</li><li>To some extent</li><li>Most of the time</li><li>Always</li><li>Not applicable</li></ol></td></tr><tr><td>HealthcareConsideration</td><td>In the context of your care, are you treated as a whole person and not reduced to a disease or health problem?</td><td><ol><li>Not at all</li><li>To some extent</li><li>Most of the time</li><li>Always</li><li>Not applicable</li></ol></td></tr><tr><td>ComplexityHealthIssues</td><td>Most health issues are too complex for me to understand.</td><td><ol><li>Strongly disagree</li><li>Disagree</li><li>Neither agree nor disagree</li><li>Agree</li><li>Strongly agree</li></ol></td></tr><tr><td>target</td><td>In the past 7 days, how often have you been bothered by emotional problems such as feeling anxious, depressed, or irritable?</td><td><ol><li>Never</li><li>Rarely</li><li>Sometimes</li><li>Often</li><li>Always</li></ol><p>Binarisation: [1, 2] values are converted 0 i.e. no mental distress, whereas [3, 4, 5] values are converted to 1, i.e. mental distress.</p></td></tr></tbody></table>

### Steps

Here are the steps followed in this demo:

{% stepper %}
{% step %}
### [Superset](superset.md)

Create customizable dashboards to gain a deeper understanding of your dataset, and utilize the embedded SQL Lab to prepare your data for the next steps.
{% endstep %}

{% step %}
### [Exploratory Module](exploratory-module.md)

Use different tools, such as [sweetViz](../../tutorials/design/exploratory-module.md#id-1.-sweetviz), to understand the underlying relationship between your data's variables and potentially delete redundant ones.
{% endstep %}

{% step %}
### [Input Module](input-module.md)

Multiple tools can be exploited in the Input Module, such as the Create Holdout Set Tool, to partition data into training and holdout sets.
{% endstep %}

{% step %}
### [Learning Module](learning-module.md)

The Learning Module represents the main step of the demo. It will be utilized to test multiple machine learning algorithms for predicting the emotional state variable, select the best-performing one, and train and save a final model.
{% endstep %}

{% step %}
### [Evaluation Module](evaluation-module.md)

In this module, we will utilize the saved machine learning model to make predictions on the holdout set and try to interpret and explain the model's choices.
{% endstep %}

{% step %}
### [Application Module](./#application-module)

This final step is similar to model deployment, where we will utilize the saved model from the Learning Module to generate predictions on new input data.
{% endstep %}
{% endstepper %}
