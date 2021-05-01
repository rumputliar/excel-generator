# Excel Random Name and Support Ticket Update Generators

In order to create a data dashboard design that analyses the performance of customer support/service agents across timezones, including the degree to which each global office provides Follow-the-Sun (FTS) support, I first needed to generate a fictional dataset for it.

I started by creating a random business, person name, and email generator in Excel, which is based on lists of popular given and surnames from a variety of major countries, and common words used in business names.

**1. Random business and people's name generator**
* [https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Random_name_and_business_generator.xlsx](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Random_name_and_business_generator.xlsx?raw=true)

By default it creates 3000 random names across 500 random businesses.

![Random name generator](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/screenshots/01.png?raw=true)

![Random business generator](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/screenshots/02.png?raw=true)

It's recommended to revise the output for duplicates or other unrealistic or undesirable data. Once the output is cleaned up, you just need the Full Name and Location details to populate the Support Ticket Update Generator.

**2. Random support ticket update generator**
* [https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Support_ticket_updates_generator_v2.xlsx](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Support_ticket_updates_generator_v2.xlsx?raw=true)

Sample output can be downloaded here:
* [https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Support_ticket_updates_v2.xlsx](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Support_ticket_updates_v2.xlsx?raw=true)

After deciding on the names to be used for the support agents, populate the relevant columns under the **Staff** worksheet (indicated in red). The columns which are autopopulated using vlookups should be left alone (e.g. *Timezone* and *Randomiser helper*). 

![Filling in support agent names in ticket update generator](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/screenshots/03.png?raw=true)

There are a number of columns representing the statistics for each agent that need to be manually defined  (indicated in blue).

![Filling in support agent statistics](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/screenshots/04.png?raw=true)

The following 3 columns are used by the **Updates 1** worksheet's *Assignee name* column to distribute tickets among agents belonging to the same *Office region*.

* *Region Agent number*: Sequential ID for each agent in the region beginning from 1 to *Number of agents in Office region* as the maximum.
* *Assignment proportion*: Number between 1 and 100. Recommend between 60 and 90.
* *Assignment break*: Number less than *Number of agents in Office region*.

The *Assignment proportion* and *Assignment break* values need to be the same for all users per *Office region*.

How it works: 

**Updates 1** randomises between 1 and 100, and if the value is:
 - Less than or equal to the *Assignment propotion*, then randomise between 1 and *Assignment break*.
 - More than *Assignment proportion*, randomise between *Assignment break* and *Number of agents in Office region*.
The *Randomiser Helper* column uses the resulting value to specify the Agent for **Updates 1**.

Using an example of:
 - Assignment proportion = 85
 - Assignment break = 5
 - Number of agents in Office region = 7

Excel's randomisation tries to distribute 85% of the ticket assignments to Region Agent numbers 1 to 5, and the remaining 15% is distributed to the remaining *Region Agent number*s 6 and 7. This allows defining data deliberate assignment trends. Otherwise, Excel will near-equally distribute the tickets.

These columns are specific to each agent.

* *Minimum responses*: Should at least be 1 (representing someone who closes tickets in a single response).
* *Maximum responses*: Should be higher than *Minimum responses* with maximum being the number of **Updates** worksheets dedicated to agent responses.
* *Assignment earliest time*: Earliest time in minutes for agent to pick up tickets.
* *Assignment latest time*: Latest time in minutes for agent to pick up tickets.
* *Minimum response time*: Earliest time in minutes for agent to reply to client.
* *Maximum response time*: Latest time in minutes for agent to reply to client.
* *Dev ticket self raise probability*: Probability the agent reports the development ticket for their support ticket.
* *Photo ID*: Optional field.
* *Photo URL*: Optional field.

Agent photos for the sample dataset are here:
* [https://github.com/datamesse/excel-support-ticket-update-generator/tree/main/agents](https://github.com/datamesse/excel-support-ticket-update-generator/tree/main/agents)

Photographs were taken from [Pixabay.com](https://pixabay.com/service/license/) and [Pexels.com](https://www.pexels.com/license/) for non-commercial use, edited to fit the appearance of an organisational profile photo, and direct URL attribution included in the dataset for each photo.

![Sample dataset agent photos](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/screenshots/05.png?raw=true)

After deciding on the names to be used for the clients, populate the relevant columns under the **Client** worksheet (indicated in red).

![Filling in client names in ticket update generator](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/screenshots/06.png?raw=true)

Then manually define the response times for each client.
* *Minimum response time*: Earliest time in minutes for client to reply to agent.
* *Maximum response time*: Latest time in minutes for client to reply to agent.

**Important notes:** 

1. All the numbers used in the *Office region* column of the **Client** worksheet must exist against at least one record for the *Office region* column of the **Agent** worksheet. This mapping process is what ensures agents exist to respond to clients.

2. Because the generators rely on Excel formula randomisation and Excel is typically defaulted to Automatic Workbook Calculation, each time the generator workbooks are opened or edited (or click Enter in a cell), new values are generated.

3. Based on the previous point, copying data from the ticket updates generator to another open Excel workbook risks the **Updates** and **Assignment** worksheets re-randomising during that process, causing discrepancies. To get around that, you can Save As each worksheet as a new tab delimited flat text file. Then copy-and-paste from those flat text files into the new Excel workbook, to avoid that problem.

A third optional Excel dataset below was extracted from Wikipedia with relative data points on when Daylight Savings are applied for different timezones and the hour offsets, which I've referred to as "anchors".

**3. Standard and Daylight Saving Observations dataset**
* [https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Time_zone_offsets_and_DST_observations.xlsx](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Time_zone_offsets_and_DST_observations.xlsx?raw=true)

You can find details on how this dataset was created using Power BI in this blog post:
[https://datamesse.github.io/blog/2021/01/23/import-time-zone-offsets-and-observation-anchors-from-wikipedia.html](https://datamesse.github.io/blog/2021/01/23/import-time-zone-offsets-and-observation-anchors-from-wikipedia.html)