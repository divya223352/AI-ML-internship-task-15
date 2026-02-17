# AI-ML-internship-task-15
What is an ML Pipeline?
An ML Pipeline is a structured sequence of data processing components. It "bundles" every step—from data cleaning and feature scaling to the final prediction—into a single object. In Python, the Pipeline class ensures that the same sequence of transformations is applied consistently to both training and production data.
2. Why do pipelines reduce Data Leakage?
Data leakage occurs when information from the test set (or future data) "leaks" into the training phase.
Without Pipelines: You might calculate the "Mean" of the entire dataset to scale it. This is a mistake because the training set now knows the "average" of the test set.
With Pipelines: The pipeline fits the scaler only on the training fold during fit(), and then applies those exact same parameters to the test set during predict().
3. What is ColumnTransformer?
It is a scikit-learn tool that allows different columns to be processed differently.
Example: You can apply StandardScaler to numerical "Age" columns and OneHotEncoder to categorical "City" columns simultaneously within the same pipeline. Without it, you would have to manually split and merge your dataframe, which is prone to errors.
4. Why do pipelines help deployment?
In production, you receive "raw" data. If you didn't use a pipeline, you would have to manually load the scaler, load the imputer, and load the model separately, ensuring they are applied in the exact same order as training.
With a pipeline, you simply call pipeline.predict(raw_data). It handles all preprocessing internally, making the production code much cleaner and less likely to crash.
