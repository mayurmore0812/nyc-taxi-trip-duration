# Dataset and input schema

Source: [New York City Taxi Trip Duration competition](https://www.kaggle.com/competitions/nyc-taxi-trip-duration/data). The [competition rules](https://www.kaggle.com/competitions/nyc-taxi-trip-duration/rules) govern access/use. Kaggle may require login and rule acceptance. A complete redistribution/licence determination is not provided; no raw data is bundled.

Place `train.csv` next to the notebook and launch Jupyter from the repository root. Alternative loader formats are `train.zip` with a root `train.csv` member, or `nyc-taxi-trip-duration.zip` with a root `train.zip` member containing `train.csv`. The nested loader expects those exact member names. A current raw taxi extract is not automatically equivalent to the competition dataset.

## Local input profile

| Input | Rows | Bytes | Target |
|---|---:|---:|---|
| train.csv | 1,458,644 | 200,589,097 | trip_duration |
| test.csv | 625,134 | 70,794,289 | None |

Training pickup datetime span: 2016-01-01 00:00:17 through 2016-06-30 23:59:39. Raw duration span: 1–3,526,282 seconds.

## Fields

`id`: trip identifier; `vendor_id`: provider code; `pickup_datetime`: pickup timestamp; `dropoff_datetime`: dropoff timestamp in labelled data; `passenger_count`: passenger count; `pickup_longitude`, `pickup_latitude`, `dropoff_longitude`, `dropoff_latitude`: recorded endpoints; `store_and_fwd_flag`: recorded storage/forwarding flag; `trip_duration`: target seconds in labelled data.

The model excludes `id` and `dropoff_datetime`; `trip_duration_min` is for exploration only and excluded from model inputs. Pickup/dropoff coordinates are assumed available for prediction. Time/location records are not redistributed individually in this repository.

## Filtering

Both endpoints must lie within longitude −74.5 to −73.25 and latitude 40.4 to 41.2. Duration must be 20–14,400 seconds inclusive. Independent inspection counted 115 coordinate exclusions, 5,598 duration exclusions and 5,705 combined exclusions, retaining 1,452,939 rows. Individual exclusion counts overlap and must not be added to calculate combined exclusions.

These are scope choices. They do not identify the causes of anomalous records, demonstrate erroneous meter/GPS readings or establish performance outside the retained population.
