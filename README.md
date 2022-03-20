# Challenge14

1. SVM Model unadjusted
# Set the short window and long window
short_window = 4
long_window = 100

# Select the ending period for the training data with an offset of 3 months
training_end = X.index.min() + DateOffset(months=3)

 precision    recall  f1-score   support

        -1.0       0.43      0.04      0.07      1804
         1.0       0.56      0.96      0.71      2288

    accuracy                           0.55      4092
   macro avg       0.49      0.50      0.39      4092
weighted avg       0.50      0.55      0.43      4092

PNG file uploaded

2. Tuning the training algorithm by adjusting the size of the training dataset
# Select the ending period for the training data with an offset of 3 months
training_end = X.index.min() + DateOffset(months=12)

precision    recall  f1-score   support

        -1.0       0.00      0.00      0.00      1497
         1.0       0.56      1.00      0.72      1931

    accuracy                           0.56      3428
   macro avg       0.28      0.50      0.36      3428
weighted avg       0.32      0.56      0.41      3428

# Select the ending period for the training data with an offset of 3 months
training_end = X.index.min() + DateOffset(years=3)

 precision    recall  f1-score   support

        -1.0       0.00      0.00      0.00       772
         1.0       0.55      1.00      0.71       948

    accuracy                           0.55      1720
   macro avg       0.28      0.50      0.36      1720
weighted avg       0.30      0.55      0.39      1720

# Select the ending period for the training data with an offset of 3 months
training_end = X.index.min() + DateOffset(years=2)
precision    recall  f1-score   support

        -1.0       0.80      0.00      0.01      1229
         1.0       0.56      1.00      0.72      1565

    accuracy                           0.56      2794
   macro avg       0.68      0.50      0.36      2794
weighted avg       0.67      0.56      0.41      2794

Increasing the training window after 2 yrs does not result in precision or recall values. However at 2 yrs, precision values for long (0.56) and short (0.80) trading is better than original model with 3 month training offset.


3. Tuning the trading algorithm by adjusting the SMA input features
# Set the short window and long window
short_window = 50
long_window = 100

# Select the ending period for the training data with an offset of 3 months
training_end = X.index.min() + DateOffset(years=2)

1.0    2305
-1.0    1819

 precision    recall  f1-score   support

        -1.0       0.45      0.31      0.36      1151
         1.0       0.56      0.70      0.62      1452

    accuracy                           0.53      2603
   macro avg       0.51      0.50      0.49      2603
weighted avg       0.51      0.53      0.51      2603

# Set the short window and long window
short_window = 10
long_window = 200
# Select the ending period for the training data with an offset of 3 months
training_end = X.index.min() + DateOffset(months=3)

1.0    2201
-1.0    1724

precision    recall  f1-score   support

        -1.0       0.44      0.95      0.60      1598
         1.0       0.59      0.06      0.11      2075

    accuracy                           0.45      3673
   macro avg       0.51      0.50      0.35      3673
weighted avg       0.52      0.45      0.32      3673

# changing the SMA window with short=10, long=200 impacts the recall (0.95) score for short trading signals.

4. Parameters that best improved the trading algorithm returns

 # depending on whether one wants to chase precision or recall or accuracy for either short strategy or long strategy the model parameters that make an impact differ. Ex. changing the short SMA=10 and long SMA=200 with 3 month training period gives the best recall (0.95) for short startegy, keeping the short SMA =4, long SMA =100 and changing the training offet to 2 yrs gives the best precision for the short strategy.
   PNG file uploaded
