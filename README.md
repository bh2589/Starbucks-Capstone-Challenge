# Starbucks Capstone Challenge

### Directory

1. [Installation](#installation)
2. [Project Motivation](#motivation)
3. [File Descriptions](#description)
4. [Conclusions](#conclusions)
5. [Licensing, Authors, and Acknowledgements](#licensing)

## Installation <a name="installation"></a>

The code should run with no issues using Python versions 3.

## Project Motivation<a name="motivation"></a>

For this project, a data set that mimics customer behavior on the Starbucks rewards mobile app is given. Once every few days, Starbucks sends out an offer to users of the mobile app. An offer can be merely an advertisement for a drink or an actual offer such as a discount or BOGO (buy one get one free). The goal of this project is to create a recommendation engine for Starbucks to decide which offers should be sent to which cohorts.

## File Descriptions <a name="description"></a>

The given data is a simplified version of the real Starbucks app because the underlying simulator only has one product whereas Starbucks actually sells dozens of products.

The data is contained in three files:
- `portfolio.json` - containing offer ids and meta data about each offer (duration, type, etc.)
- `profile.json` - demographic data for each customer
- `transcript.json` - records for transactions, offers received, offers viewed, and offers completed

Here is the schema and explanation of each variable in the files:

`portfolio.json`
- id (string) - offer id
- offer_type (string) - the type of offer ie BOGO, discount, informational
- difficulty (int) - the minimum required to spend to complete an offer
- reward (int) - the reward is given for completing an offer
- duration (int) - time for the offer to be open, in days
- channels (list of strings)

`profile.json`
- age (int) - age of the customer
- became_member_on (int) - the date when customer created an app account
- gender (str) - gender of the customer (note some entries contain 'O' for other rather than M or F)
- id (str) - customer id
- income (float) - customer's income

`transcript.json`
- event (str) - record description (ie transaction, offer received, offer viewed, etc.)
- person (str) - customer id
- time (int) - time in hours since the start of the test. The data begins at time t=0
- value - (dict of strings) - either an offer id or transaction amount depending on the record

## Conclusions<a name="conclusions"></a>

The main findings of the code can be found at the post available [here](https://medium.com/@bh2589/starbucks-offers-wont-be-surprising-anymore-f10543dac109).

For the first part of this project, a user-item-matrix that represents how users responded to the offers they received was built. And then, the records was splitted into training set and test set. By using SVD, a model was trained to predict how a user responses to a particular offer. We achieved a lowest mean square error of 0.002254 for a 15-latent-feature model trained by the training set , and we achieved a lowest mean square error of 0.3354 for a 5-latent-feature model trained by the testing set. After that, we created a recommendation engine for Starbucks to decide which offer should be sent to which cohort.

For the second part of this project, some demographic data exploration was implemented. Some fun facts are: Female cohort responds much better than male cohort, upon receiving both BOGO and discount offer. Male cohort reacts slightly better to discount than BOGO. Also, a better way is via social media. Among all ten offers, sending the offer "buy 10 dollars get 2 dollars off within 10 days" via email, web, mobile and social makes Starbucks gain more. 


