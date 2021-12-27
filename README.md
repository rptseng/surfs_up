# surfs_up_analysis
## Background
We will use SQLAlchemy to query a data set and compare the weather patterns between June and December in Oahu. The goal is to see if a surf and ice cream shop business is sustainable year-round.

## Results
Below are the two summary DataFrames for June and December.
- The mean temperature is higher in June than December by four degrees (75F vs 71F).
- The standard deviation in June temperatures are smaller than December temperatures (3.75 vs 3.25), meaning the weather is more variable during the month of December.
- The sample size in June is larger than December by 183 temperature observances (1700 vs 1517), so there is a possibility we are missing records for a particular weather station location.

### June DataFrame Summary
![june_df_summary.png](https://github.com/rptseng/surfs_up/blob/main/june_df_summary.png)

### December DataFrame Summary
![december_df_summary.png](https://github.com/rptseng/surfs_up/blob/main/december_df_summary.png)

## Summary
In reviewing the results, although there are some differences between June and December temperatures in Oahu, they may not be large enough to determine whether a surf and ice cream business can be run year-round. To supplement this analysis, we can run additional queries on precipitation between these two periods if we assume rain will negatively correlate to ice cream sales. We may also want to run queries on other months of the year, like September, to build more robust picture of year-round weather conditions.

### June Precipitation Query
session.query(Measurement.date, Measurement.prcp).\
filter(extract('month', Measurement.date) == 6).all()

### December Precipitation Query
session.query(Measurement.date, Measurement.prcp).\
filter(extract('month', Measurement.date) == 12).all()

### September Temperature Query
session.query(Measurement.date, Measurement.tobs).\
filter(extract('month', Measurement.date) == 9).all()