# **Data Dictionary for Yellow Taxi Trip Data**

This document outlines the data dictionary for the yellow taxi trip dataset. The dictionary has been updated to include selected columns, derived metrics, and additional comments based on our transformation process.

---

## **Columns**

| Column Name             | Data Type     | Description                                                                                  | Transformation / Notes                                      |
|-------------------------|---------------|----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| **Trip_Pickup_DateTime**  | `datetime`    | Timestamp of when the trip started.                                                          | Convert to `datetime` during transformation.               |
| **Trip_Dropoff_DateTime** | `datetime`    | Timestamp of when the trip ended.                                                            | Convert to `datetime` during transformation.               |
| **Passenger_Count**       | `int`         | Number of passengers during the trip.                                                        | Remove invalid or extreme values (e.g., >10).              |
| **Trip_Distance**         | `float`       | Distance of the trip in miles.                                                               | Validate for non-negative values and reasonable distances. |
| **Start_Lon**             | `float`       | Longitude of the trip's pickup location.                                                     | Validate geographic range (-180 to 180).                   |
| **Start_Lat**             | `float`       | Latitude of the trip's pickup location.                                                      | Validate geographic range (-90 to 90).                     |
| **End_Lon**               | `float`       | Longitude of the trip's dropoff location.                                                    | Validate geographic range (-180 to 180).                   |
| **End_Lat**               | `float`       | Latitude of the trip's dropoff location.                                                     | Validate geographic range (-90 to 90).                     |
| **Fare_Amt**              | `float`       | Base fare amount for the trip.                                                               | Validate for non-negative values.                          |
| **Total_Amt**             | `float`       | Total fare amount, including tips, tolls, and additional charges.                            | Validate for non-negative values.                          |

---

## **Derived Columns**

| Column Name             | Data Type     | Description                                                                                  | Transformation / Notes                                      |
|-------------------------|---------------|----------------------------------------------------------------------------------------------|-----------------------------------------------------------|
| **trip_duration_minutes** | `float`       | Duration of the trip in minutes, calculated as the difference between pickup and dropoff times. | Derived during transformation.                             |
| **average_speed_kmph**    | `float`       | Average speed of the trip in kilometers per hour, calculated as `(Trip_Distance / Trip_Duration) * 60`. | Derived during transformation.                             |

---

## **Notes**

1. **Dropped Columns**: Non-essential columns such as `Rate_Code`, `store_and_forward`, and `mta_tax` are excluded for this analysis.
2. **Datetime Conversion**: Ensure both `Trip_Pickup_DateTime` and `Trip_Dropoff_DateTime` are parsed as `datetime` objects.
3. **Data Validation**: Rows with invalid or extreme values in numeric columns (e.g., `Passenger_Count`, `Trip_Distance`) will be removed or imputed.
4. **Geographic Validation**: Longitude and latitude values will be checked to ensure they fall within valid geographic ranges.