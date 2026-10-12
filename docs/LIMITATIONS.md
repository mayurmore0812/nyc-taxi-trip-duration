# Limitations

## Preprocessing and model selection

- **Clustering before the split:** cell 51 fits MiniBatchKMeans on all filtered pickup/dropoff coordinates before cell 54 creates the training, validation and test partitions. The target is not used, but validation/test coordinates influence a learned transformation. The full workflow is therefore not strictly training-only preprocessing.
- **Winner-name condition:** cell 83 compares `best_name` with `RFR`, while the comparison label is `Random Forest Regressor`. With the current labels, the branch selects `hgb_best`. If Random Forest wins validation, the displayed name can differ from the evaluated estimator. In the currently saved output, the displayed final model is Hist Gradient Boosting Regressor.
- **Retained parameter grids:** each final tuning grid contains one configuration. The notebook does not rerun the broader historical search, and the saved run does not by itself establish that each engineered feature improves performance.

## Evaluation population

- The random 70/15/15 split measures performance on held-out trips from the same historical pool, rather than a later time period or current traffic conditions.
- Coordinate exclusions and the 20-second–4-hour duration rule restrict the evaluated population. They do not prove every excluded trip is false or true.
- Duration filtering uses the observed target to define the study population; it is not an operational pre-trip validity rule.
- Pickup/dropoff endpoints are assumed available inputs. Straight-line and Manhattan-style distances are approximations, not measured driven routes.

## Operational interpretation

- Traffic, weather, roadworks, demand and actual route conditions are not observed.
- Aggregate error metrics can hide weaker performance on long or unusual trips; duration-group results are relevant to interpretation.
- Saved outputs document an executed run, but do not establish identical results in a fresh environment or on different data. Exact package versions are not locked.
- No measured latency, peak-memory benchmark, trained-model export, live dispatch integration or quantified business benefit is provided.
- An internal test result is not a guarantee of deployment performance or robustness to changing travel patterns.
