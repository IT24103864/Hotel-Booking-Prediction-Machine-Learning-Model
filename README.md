# Hotel-Booking-Prediction-Machine-Learning-Model
Hotel Booking Prediction Machine Learning Model
# Hotel Booking Cancellation Prediction

A machine learning project that predicts which hotel bookings are likely to be canceled. A cancellation risk score can help hotel teams prioritize follow-up and plan room availability.

**Tools:** Python · Jupyter Notebook · pandas · NumPy · scikit-learn · imbalanced-learn · Matplotlib · Seaborn

[Open the notebook](hotel_booking_cancellation_prediction_1.ipynb) · [Watch the project demo](https://youtu.be/OUAWTreQeyM)

## 📊 Dataset

The included [hotel booking dataset](hotel_bookings.csv) contains **119,390 bookings and 32 columns** before cleaning. The notebook uses **87,011 records** after cleaning and splits them into **69,608 training records** and **17,403 test records**.

The prediction target is `is_canceled`, where `1` means the booking was canceled and `0` means it was kept.

## 🔍 Machine learning workflow

1. **Explore and clean the data.** Inspect missing values, duplicates, and invalid entries. Explore how cancellation rates vary across booking characteristics.
2. **Engineer features.** Derive total nights, total guests, lead-time groups, and a special-request indicator.
3. **Build preprocessing pipelines.** Fit imputation, encoding, and scaling on training data within each cross-validation fold.
4. **Compare models.** Evaluate Logistic Regression, K-Nearest Neighbors, Decision Tree, Random Forest, and Linear SVC against a majority-class baseline using 5-fold stratified cross-validation.
5. **Handle class imbalance and tune models.** Compare class weighting with SMOTENC and an unadjusted baseline. Use F1 to guide hyperparameter tuning.
6. **Evaluate the final model.** Measure performance on the held-out test set and examine the confusion matrix, feature importance, and threshold trade-offs.

## 📈 Results

**Tuned Random Forest** was the final model. These scores come from the saved notebook output for the held-out test set at a classification threshold of **0.50**.

| Metric | Test score |
| --- | ---: |
| Accuracy | 83.3% |
| Precision | 66.2% |
| Recall | 80.5% |
| F1 score | 72.6% |
| ROC-AUC | 0.909 |
| PR-AUC | 0.794 |

The model flagged **3,852 of 4,786** cancellations in the test set. The notebook also uses a room-type change feature derived from reserved and assigned rooms. For booking-time use, confirm that the assigned room is available when predictions are made. If it becomes available later, remove that feature and re-evaluate the model.

## 🛠️ Run the project locally

1. Download or clone the repository. Keep `hotel_bookings.csv` in the same folder as the notebook.
2. Open a terminal in that folder and install the dependencies.

   ```bash
   python -m pip install notebook numpy pandas matplotlib seaborn scikit-learn imbalanced-learn
   ```

3. Launch Jupyter Notebook.

   ```bash
   python -m notebook
   ```

4. Open `hotel_booking_cancellation_prediction_1.ipynb` and run the cells from top to bottom. Cross-validation and hyperparameter tuning may take several minutes.

## 📁 Project files

| File | Contents |
| --- | --- |
| [hotel_booking_cancellation_prediction_1.ipynb](hotel_booking_cancellation_prediction_1.ipynb) | Data analysis, preprocessing, model training, and evaluation |
| [hotel_bookings.csv](hotel_bookings.csv) | Input dataset |
| [2026_DS_46_Final_Report.docx](2026_DS_46_Final_Report.docx) | Full assignment report |
