# Data-Analysis-Global-Shark-Attacks

**Goals:** 

After an initial look to the context and the available data, the valuable information will contain:
- The time with more attacks
- The place(s) with more attacks
- The most common activity(ies) which led to the attack
- The gender most attacked
- The average age of the victim
- The rate of death

The final objective would be to find :
- Which gender, at what age, doing what in which part of the world has the highest risk of beeing attacked by a shark.
- In what percentage the attack results in an injury or a death ?


**Data Cleaning:** 

- First, Remove duplicates and Reshape columns.
- Second, Clean each columns. 

For columns which will not be used for the analysis I only replaced NaN by "unknown".

For the usefull ones : 
- In column year I kept only the valid years and fill the NaN with the information available in the column "Date" when available
- In column countries and areas I removed typos
- In column fatal(y/n) the answer to many NaN was in the injury column. With a loop I added Y to the Fatal column when in the column injury it was finding the word "fatal". Else: N. When no info in injury, I updated the data with "unknown".
- I categorised the column Activites into :
    Paddling
    boating
    falling
    fishing
    surfing
    swimming
    When the activity did not seem to enter in one of those, it entered the category "other"
- Cleaning Age column:
    Often the numerical value has a "s" at the end to mark it's year range. I removed it to keep a numerical type. 
    All text cells without numbers and withouth the term "teen" were renamed "unknown".
    Then all years were categorised between their range : 
        0s, 10s, 20s, ..., 90s.
- Cleaning Time column:
   Through regex I identified the hh:mm
   Then I kept only the hours. 
   I kept the hours in a new column called "Time_Range".
    
    
    
**IV Cleaning : Done. Now let's get into the analysis !**

- Based on our objtectives we need to exploit the following collumns :
    year - Time_Range - sex- Range_Age - country - area - Activities_Count

I created a formula sheet with a check_unkowns formula.
Based on it, in order of appearance above, we have : 
    The ratio of unkowns is  0.0 %
    The ratio of unkowns is  63.30041414463204 %
    The ratio of unkowns is  8.935966868429436 %
    The ratio of unkowns is  45.89041095890411 %
    The ratio of unkowns is  0.7645747053201656 %
    The ratio of unkowns is  7.167887862376553 %
    The ratio of unkowns is  1.1309334182860784 %
    The ratio of unkowns is  0.0 %
    
Based this test, the time_range will be based on a sample less representative than the others.
#A part from time_range, the data represent at leat 50%+ of the lines.

- New data frame:
To optimise the analysis I created a new data frame with our 8 relevant collumns: 


- Results :

The most representative datas are:
- 2015
- Male
- USA
- Florida
- Not Fatal
- Swimming

The hour most fatal is between 15h and 16h. Seems like sharks like snaking.
The hour with most non fatal attacks is between 11h and 12h. Seems that sharks lunch at German time.
The hour with most attacks is btwn 11h and 12h.


Men have much more incidents than women.
Women, in proportion, are less killed than men during attacks
    Male percentage of fatal accident = 23.838582677165356 %
    Femal percentage of fatal accident = 17.29559748427673 %


Teens are the most attacked. Closely followed by 20s.
Teens are also the most killed followed closely by 20s.

The most attacked country is USA with 2225 attacks.
The most attacked zone is Florida with 1035 attacks
Outside USA, the most attacked area is New South Wales which is in Australia.

The percentage of death during an attack is 30%.

The swimmers are the most attacked. 
The swimmers are also the more killed.
Intersting to observe how surfers tend to escape the death in bigger proportion than the rests.
    percentage of surfers killed by the attack 5.88703261734288 %


Therefore, the highest probability of death was to be a male teenager, swimming in Florida in 2015 from 11 to 12am. If attacked the boy would have 18% chances of survival.

