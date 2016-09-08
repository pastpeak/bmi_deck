---
title       : Body Mass Index (BMI) Calculator
subtitle    : A calculator for Body Mass Index (BMI) to demonstrate shiny and slidify.
author      : Jon Ide 
job         : Coursera Student
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---

## Body Mass Index

### According to Wikipedia:

"The body mass index (BMI) or Quetelet index is a value derived from the mass (weight) and height of an individual. The BMI is defined as the body mass divided by the square of the body height, and is universally expressed in units of kg/m2, resulting from mass in kilograms and height in metres."

For a largely American audience, we will use pounds and inches instead, which requires multiplying weight divided by the square of height by a factor of 703.

<b>Just enter your weight in pounds and height in inches, and the BMI Calculator does the rest!</b>

--- 

## Interpretation of BMI

The shiny app takes height in inches and weight in pounds, calculates and displays the BMI, and also displays an interpretation of the BMI. The interpretation used in the app is one that applies to average adults of European descent. For people of Asian descent, for example, or for children, a different interpretation would need to be used.

The interpretation:<br>
BMI < 18.5: underweight<br>
BMI 18.5 - 25.0: normal<br>
BMI 25.0 - 30.0: overweight<br>
BMI > 30.0: obese.

Note that people with greater-than-average amounts of muscle (athletes, for example) often have BMI values that would classify them as overweight or even obese, when they are anything but.

<h3><span style="color:red">Where do you stand? Use the BMI Calculator to find out!</span></h3>

---

## R Code

We define an R function to calculate BMI, as follows:


```r
bmi <- function(inches, pounds) round(pounds / inches^2 * 703, digits=1)
```

And for the interpretation of BMI, we define:


```r
interpretation <- function(bmi) {
  if (bmi < 18.5) {
    status <- 'Underweight'
  } else if (bmi < 25) {
    status <- 'Normal or Healthy Weight'
  } else if (bmi < 30) {
    status <- 'Overweight'
  } else {
    status <- 'Obese'
  }
  paste0('Your BMI (', bmi, ') has interpretation: ', status, collapse)
}
```

---

## Sample Calculations

George Clooney is 71 inches tall and weighs 172 pounds. What's his BMI?


```r
interpretation(bmi(71, 172))
```

```
## [1] "Your BMI ( 24 ) has interpretation:  Normal or Healthy Weight"
```
<p>
Dwayne Johnson ("The Rock") is 74 inches tall and weighs 260 pounds. His BMI:


```r
interpretation(bmi(74, 260))
```

```
## [1] "Your BMI ( 33.4 ) has interpretation:  Obese"
```

This is an example of the effect mentioned earlier: BMI can be very misleading for people with a lot of muscle. I choose to believe that explains my BMI! :-)
