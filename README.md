# Election Analysis Challenge 

## Project Overview 
 A Colorado Board of Elections employee has given us the following tasks to complete the election audit of a recent local congressional election.

The county calculations have to be included in additon to the exsiting candidate results
 1. Calculate the total number of votes cast.
 2. Get a complete list of **counties** who receieved votes.
 3. Get a complete list of candidates who receieved votes.
 4. Calculate the total number of votes each **counties** received.
 5. Calculate the total number of votes each candidate received.
 6. Calculate the percentage of votes each **county** won.
 7. Calculate the percentage of votes each candidate won.
 8. Determine the winner of the **county** based on popular vote.
 9. Determine the winner of election based on popular vote.

 ## Resources 
 - Data Source : election_results.csv
 - Software Python 3.9.12 , Visual Studio code 1.72.2

## File Output
 - Analysis folder : election_analysis.txt

## Code snippets for county analysis 
- Calculated county details based of the county options

```python
if county_name not in county_options:
    # 4b: Add the existing county to the list of counties.
    county_options.append(county_name)

    # 4c: Begin tracking the county's vote count.
    county_votes[county_name] = 0

 # 5: Add a vote to that county's vote count.
 county_votes[county_name] += 1
```
- Winning county calculation
```python
for county_name in county_votes:
        # 6b: Retrieve the county vote count.
        c_votes = county_votes.get(county_name)

        # 6c: Calculate the percentage of votes for the county.
        c_vote_percentage = float(c_votes) / float(total_votes) * 100
        
        county_results = (
            f"{county_name}: {c_vote_percentage:.1f}% ({c_votes:,})\n")

         # 6d: Print the county results to the terminal.
        print(county_results)

         # 6e: Save the county votes to a text file.
        txt_file.write(county_results)
         # 6f: Write an if statement to determine the winning county and get its vote count.
        if (c_votes > winning_county_count) and (c_vote_percentage > winning_county_percentage):
            winning_county_count = c_votes
            winning_county = county_name
            winning_county_percentage = c_vote_percentage

    # 7: Print the county with the largest turnout to the terminal.
    winning_county_summary = (
        f"\n--------------------------\n"
        f"Largest County Turnout : {winning_county}\n"
        f"--------------------------\n\n")
    print(winning_county_summary)
```

 ## Election Audit Results 
 The analysis of the election show that:

- There were a total of 369,711 votes cast in the election

    - The Counties were
        - Jefferson
        - Denver
        - Arapahoe

    - The County results were :
        - Jefferson received 10.5% ofthe vote and 38,855 of votes.
        - Denver received 82.8% ofthe vote and 306,055 of votes.
        - Arapahoe received 6.7% ofthe vote and 24,801 of votes.

    - The Largest County Turnout was :
            Denver

    - The Candidates were
        - Charles Casper Stockham 
        - Diana DeGette
        - Raymon Anthony Doane

    - The candidate results were :
        - Charles Casper Stockham received 23.0% ofthe vote and 85,213 of votes.
        - Diana DeGette received 73.8% ofthe vote and 272,892 of votes.
        - Raymon Anthony Doane received 3.1% ofthe vote and 11,606 of votes.
    
    - The winner of the election was :
        - candidate Diana DeGette, who receieved 73.8% ofthe vote and 272,892 of votes.

### Command Line Output of PyPoll Challenge
![img](https://github.com/hsurisetti/ElectionAnalysis_Challenge/blob/main/CommandLinePyPollResults.png)

### File Output of PyPoll challenge
![img](https://github.com/hsurisetti/ElectionAnalysis_Challenge/blob/main/FileOutputPyPollResults.png)

## Election Audit Summary

  In Summary, the election audit script has been prepared which is user friendly, the code has been formatted appropriately and comments are included in every place where it is needed to easily guide the developer who is looking at the code to make any new changes. This is essential for any software application since it will help in adding any new functionlities within less amount time on top of the existing one and refactoring would be minimal.  
        
  The script can be easily modified to include any additonal details of election results.
  
  **Example 1:**
  
  If there is a new column added in the input csv file and we need to calculate and process that field , list of things that can be done easily in the code with which, the developer can easily re-use the same piece code and can derive any additonal details which might be needed later on!
  
   - initialize the appropriate list and dictionaries in the code initalizations area
   - get the new field from csv file along with others in the *with open(file_to_load)* section
   - do the calulations which are needed for it based of the options 
   - write to file output in *with open(file_to_save, "w") * section
     
   **Example 2:**
   
   If we need to change some calulations for any field later on, the comments and code formatting would easily guide to the appropriate place and the developer and modify with appropraite details.

  Finally, we have presented all the required and the additional county details for the election audit of a recent local congressional election.
