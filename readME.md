### By Eric Neugeboren
### For The Diamondback

## Data Cleaning:

The Diamondback obtained political donations data from the Federal Elections Commission and the Maryland Campaign Reporting Information System. These databases track individual political donations to federal, state and local campaigns and committees.

For both databases, we limited the dates of the contributions from 2013 to 2022. This meant the analysis would consist of donations from the past decade. The data also filtered the data from both sources for individuals who listed the University of Maryland as their employer.

The Diamondback has maintained an annual salary guide since 2013. We used this data to match employee donations to employee salaries.

Some names were slightly inconsistent across datasets but were near matches, so we changed the format of employee names on both salary and donations spreadsheets. This was necessary to match an individual’s political donation with their title and salary at the University of Maryland. To do so, we used `stringr` functions — `str_split_fixed` was used to divide a contributor’s name into three fields: first name, last name, and any extraneous parts of a name (such as middle initial or title). The `str_replace` function removed any commas in the names.

The next step was joining the datasets. We joined together the FEC data, salary guide data and  state-level data. We joined the datasets by “first name” and “last name,” which ensured the people included in the resulting dataset were University of Maryland salaried employees who submitted political donations in a given year. We repeated this process from 2013 to 2022.

## Analysis: 

FEC and state databases do not include party affiliations for campaigns or committees. Because of this, we manually assigned party affiliations to donors using resources such as ballotpedia.org, opensecrets.org, and candidate profiles on federal and state government websites. Some committees were not directly related to a party, so they were coded as nonpartisan. 

Other analyses included determining where the donations came from at the university. To do so, we grouped the data by university division, which showed us the number of donations that came from employees at particular university division, such as a specific college or entity like Student Affairs and Facilities Management. We also grouped the data by year of the contribution and employee name, and summed the donations in a given year.
