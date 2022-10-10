# 🚜 Predicting the Sale Price of Bulldozers using Machine Learning

In this notebook, we're going to go through an example machine learning project with the goal of predicting the sale price of bulldozers.

## 1. Problem definition
How well can we predict the future sale price of a bulldozer, given its characteristics and previous examples of how much similar bulldozers have been sold for?

## 2. Data
The data is downloaded from the Kaggle Bluebook for Bulldozers competition: https://www.kaggle.com/c/bluebook-for-bulldozers/data

There are 3 main datasets:

Train.csv is the training set, which contains data through the end of 2011. Valid.csv is the validation set, which contains data from January 1, 2012 - April 30, 2012 You make predictions on this set throughout the majority of the competition. Your score on this set is used to create the public leaderboard. Test.csv is the test set, which won't be released until the last week of the competition. It contains data from May 1, 2012 - November 2012. Your score on the test set determines your final rank for the competition.

## 3. Evaluation
The evaluation metric for this competition is the RMSLE (root mean squared log error) between the actual and predicted auction prices.

For more on the evaluation of this project check: https://www.kaggle.com/c/bluebook-for-bulldozers/overview/evaluation

Note: The goal for most regression evaluation metrics is to minimize the error. For example, our goal for this project will be to build a machine learning model which minimises RMSLE.

## 4. Features
Kaggle provides a data dictionary detailing all of the features of the dataset.

Data Dictionary :
1. SalesID: unique identifier of a particular sale of a machine at auction
2. MachineID: identifier for a particular machine; machines may have multiple sales
3. ModelID: identifier for a unique machine model (i.e. fiModelDesc)
4. datasource: source of the sale record; some sources are more diligent about reporting attributes of the machine than others.
5. auctioneerID: identifier of a particular auctioneer, i.e. company that sold the machine at auction. Not the same as datasource.
6. YearMade: year of manufacturer of the Machine
7. MachineHoursCurrentMeter: current usage of the machine in hours at time of sale (saledate); null or 0 means no hours have been reported for that sale
8. UsageBand: value (low, medium, high) calculated comparing this particular Machine-Sale hours to average usage for the fiBaseModel; e.g. 'Low' means this machine has less hours given it's lifespan relative to average of fiBaseModel.
9. Saledate: time of sale
10. Saleprice: cost of sale in USD
11. fiModelDesc: Description of a unique machine model (see ModelID); concatenation of fiBaseModel & fiSecondaryDesc & fiModelSeries & fiModelDescriptor
12. fiBaseModel: disaggregation of fiModelDesc
13. fiSecondaryDesc: disaggregation of fiModelDesc
14. fiModelSeries: disaggregation of fiModelDesc
15. fiModelDescriptor: disaggregation of fiModelDesc
16. ProductSize: Don't know what this is
17. ProductClassDesc: description of 2nd level hierarchical grouping (below ProductGroup) of fiModelDesc
18. State: US State in which sale occurred
19. ProductGroup: identifier for top-level hierarchical grouping of fiModelDesc
20. ProductGroupDesc: description of top-level hierarchical grouping of fiModelDesc
21. Drive_System machine configuration: typcially describes whether 2 or 4 wheel drive
22. Enclosure machine configuration: does machine have an enclosed cab or not
23. Forks machine configuration: attachment used for lifting
24. Pad_Type machine configuration: type of treads a crawler machine uses
25. Ride_Control machine configuration: optional feature on loaders to make the ride smoother
26. Stick machine configuration: type of control
27. Transmission machine configuration: describes type of transmission; typically automatic or manual
28. Turbocharged machine configuratio:- engine naturally aspirated or turbocharged
29. Blade_Extension machine configuration: extension of standard blade
30. Blade_Width machine configuration: width of blade
31. Enclosure_Type machine configuration: does machine have an enclosed cab or not
32. Engine_Horsepower machine configuration: engine horsepower rating
33. Hydraulics machine configuration: type of hydraulics
34. Pushblock machine configuration: option
35. Ripper machine configuration: implement attached to machine to till soil
36. Scarifier machine configuration: implement attached to machine to condition soil
37. Tip_control machine configuration: type of blade control
38. Tire_Size machine configuration: size of primary tires
39. Coupler machine configuration: type of implement interface
40. Coupler_System machine configuration: type of implement interface
41. Grouser_Tracks machine configuration: describes ground contact interface
42. Hydraulics_Flow machine configuration: normal or high flow hydraulic system
43. Track_Type machine configuration: type of treads a crawler machine uses
44. Undercarriage_Pad_Width machine configuration: width of crawler treads
45. Stick_Length machine configuration: length of machine digging implement
46. Thumb machine configuration: attachment used for grabbing
47. Pattern_Changer machine configuration: can adjust the operator control configuration to suit the user
48. Grouser_Type machine configuration: type of treads a crawler machine uses
49. Backhoe_Mounting machine configuration: optional interface used to add a backhoe attachment
50. Blade_Type machine configuration: describes type of blade
51. Travel_Controls machine configuration: describes operator control configuration
52. Differential_Type machine configuration: differential type, typically locking or standard
53. Steering_Controls machine configuration: describes operator control configuration
Note that a particular datasource may report on multiple auctioneerIDs
