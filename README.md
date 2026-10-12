# NYC Taxi Trip Duration Prediction

> **Repository status:** README-only preview. The project python notebook and data have not been published here yet. Results will be added after the workflow is cleaned and rerun.


## Approach

I have feature engineered location and time features, including trip distance, bearing, airport proximity, calendar indicators, and location zones. The notebook compares a Ridge regression baseline with Random Forest and histogram gradient boosting pipelines, then examines errors across trip-duration groups.

The separate competition test file has no duration labels; the notebook's internal evaluation uses a split of the labelled training data.


## Planned release

- One canonical notebook and a concise data guide
- Environment and run instructions
- Revalidated model-comparison table and selected error plots

**Tools used:** Python, pandas, NumPy, scikit-learn, matplotlib, seaborn.

**Code and data are not yet available in this repository.**
