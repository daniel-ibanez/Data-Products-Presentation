RMS Titanic - Would you have survived?
========================================================
author: Daniel Ibanez
date: 10/25/2015
transition: fade
transition-speed: slow



Goal and Solution
========================================================
<small>
The goal of this app was to demonstrate the basic functionality 
of shiny, highlighting features such as:

- Simple Interaction (reactivity)
- Use of dataset for prediction
- Use R code calculations
- Styling using the **shinythemes** library

Using data fro the Titanic dataset (part of the **datasets** library), 
my app predicts your chances of survival based on who you are and how you travel.
The construction of the app required 3 steps:

- Data cleaning and formulas for prediction
- Construction of a simple UI
- Logic for interactivity (reactivity in shinny)
</small>

Code Samples 1 of 2
========================================================
<small>
The logic behind the prediction is very simple, I started by loading the Titanic dataset.

```r
library(datasets)
data = Titanic
str(data)
```

```
 table [1:4, 1:2, 1:2, 1:2] 0 0 35 0 0 0 17 0 118 154 ...
 - attr(*, "dimnames")=List of 4
  ..$ Class   : chr [1:4] "1st" "2nd" "3rd" "Crew"
  ..$ Sex     : chr [1:2] "Male" "Female"
  ..$ Age     : chr [1:2] "Child" "Adult"
  ..$ Survived: chr [1:2] "No" "Yes"
```
Unfortunately, the dataset comes as a 4 dimensional table, hard to use for prediction purposes, 
so I cleaned the data by loading **dplyr** and converting it to a data frame.
</small>


Code Samples 2 of 2
========================================================
<small>

```r
library(dplyr)
data = data.frame(data)
head(data,3)
```

```
  Class  Sex   Age Survived Freq
1   1st Male Child       No    0
2   2nd Male Child       No    0
3   3rd Male Child       No   35
```
Now the data is in a format that through dplyr can be queried lie this:

```r
#Number of Male, Adult, 2nd Class survivors?
sum(data$Freq[data$Class=="2nd" & data$Sex=="Male" & data$Age=="Adult" & data$Survived=="Yes"])
```

```
[1] 14
```

</small>

Conclusion
========================================================
<small>
What we learned about shinny by building this app:
</small>


Pros | Cons
--- | ---
Very easy to create Data Products by extending an R model into a Web app | Easy for simple interactions, becomes difficult for more complex solutions as the **reactivity** concept is obscure
Has a nice set of input options | Direct formatting is offered through limited to **builder** elements, beyond that you have to deal directly with HTML and CSS

<small>
I can definitely see the value for prototyping and simple solutions for shiny, beyond that, a combination of **Python** with **Pandas** and **scikit-learn** seems like a much better solution.
</small>




