# Excel Random Name and Support Ticket Update Generators

In order to create a data dashboard design that analyses the performance of customer support/service agents across timezones, including the degree to which each global office provides Follow-the-Sun (FTS) support, I first needed to generate a fictional and randomised dataset for it.

I started by creating a random business, person name, and email generator in Excel, which is based on lists of popular given and surnames from a variety of major countries, and common words used in business names.

**1. Random business and people's name generator**

<ul>
  <li>
[Download here](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Random_name_and_business_generator.xlsx?raw=true)

By default it creates 3000 random names across 500 random businesses.

![Random name generator](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/screenshots/01%20Random%20name%20generator.png?raw=true)

![Random business generator](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/screenshots/02%20Random%20business%20generator.png?raw=true)

The Random Name generator can be quite, well random. So it's best to revise the output by checking how frequent certain names are to avoid duplicates. Once the output is cleaned up, you just ned the Full Name and Location details for the Support Ticket Update Generator.
  </li>
</ul>

2. Random support ticket update generator
* [https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Support_ticket_updates_generator_v2.xlsx](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Support_ticket_updates_generator_v2.xlsx?raw=true)

A sample file of the output can be found here
* [https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Support_ticket_updates_v2.xlsx](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Support_ticket_updates_v2.xlsx?raw=true)

You can find details on how these generators work in this blog post:
https://datamesse.github.io/blog/2021/02/27/support-ticket-update-times-dataset-generator-in-excel.html

A third Excel file has a dataset extracted from Wikipedia with relative data points on when Daylight Savings gets applied for different timezones and the hour offsets, which I've referred to as anchors.

3. Standard and Daylight Saving Observations dataset
* [https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Time_zone_offsets_and_DST_observations.xlsx](https://github.com/datamesse/excel-support-ticket-update-generator/blob/main/Time_zone_offsets_and_DST_observations.xlsx?raw=true)

You can find details on how this dataset was created from Power BI in this blog post:
https://datamesse.github.io/blog/2021/01/23/import-time-zone-offsets-and-observation-anchors-from-wikipedia.html

Agent photos can be found in this directory
* https://github.com/datamesse/excel-support-ticket-update-generator/tree/main/agents

**Important notes:** Because the generators rely on Excel formula randomisation and Excel is typically defaulted to Automatic Workbook Calculation, each time the generator workbooks are opened or edited, new values are generated.
