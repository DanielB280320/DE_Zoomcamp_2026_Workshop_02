# DE Zoomcamp 2026 | Workshop 02

<b>1.</b> Within the execution for Yellow Taxi data for the year 2020 and month 12: what is the uncompressed file size (i.e. the output file yellow_tripdata_2020-12.csv of the extract task)?

    Answer: 134.5 MiB

![screenshot](/screenshots/question1.png) 

<b>2.</b> What is the rendered value of the variable file when the inputs taxi is set to green, year is set to 2020, and month is set to 04 during execution?

    Answer: green_tripdata_2020-04.csv

<b>3.</b> How many rows are there for the Yellow Taxi data for all CSV files in the year 2020?
     
    Answer: 24,648,499

    SELECT 
        COUNT(*) AS NoRecords2020 
    FROM `zoomcamp_bq_dataset.yellow_tripdata`
    WHERE filename LIKE 'yellow_tripdata_2020%'
    ;

<b>4.</b> How many rows are there for the Green Taxi data for all CSV files in the year 2020?

    Answer: 1,734,051

    SELECT 
        COUNT(*) AS NoRecords2020 
    FROM `zoomcamp_bq_dataset.green_tripdata`
    WHERE filename LIKE 'green_tripdata_2020%'
    ;

<b>5.</b> How many rows are there for the Yellow Taxi data for the March 2021 CSV file?

    Answer: 1,925,152

    SELECT 
        COUNT(*) AS NoRecords_202103 
    FROM `zoomcamp_bq_dataset.yellow_tripdata`
    WHERE filename LIKE 'yellow_tripdata_2021-03%'
    ;

<b>6.</b> How would you configure the timezone to New York in a Schedule trigger?

    Answer: Add a timezone property set to America/New_York in the Schedule trigger configuration

    triggers:
    - id: green_schedule
        type: io.kestra.plugin.core.trigger.Schedule
        cron: "0 9 1 * *"
        timezone: America/New_York
        inputs:
        taxi: green

    - id: yellow_schedule
        type: io.kestra.plugin.core.trigger.Schedule
        cron: "0 10 1 * *"
        timezone: America/New_York
        inputs:
        taxi: yellow