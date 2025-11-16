# Mobile Data Price Prediction - Project Summary

## 📱 Project Overview

This project analyzes mobile phone pricing using machine learning to identify key features that impact price and build accurate prediction models.

### Dataset Information
- **Total Phones**: 541
- **Features**: 11 (including target variable 'Price')
- **Price Range**: ₹920 - ₹80,999
- **Mean Price**: ₹16,228
- **Median Price**: ₹13,499
- **Missing Values**: None

---

## 🔑 Key Features Analyzed

### Numeric Features
1. **Memory (Storage)**: 16GB - 256GB
2. **RAM**: 2GB - 8GB
3. **Battery Capacity**: 800mAh - 7000mAh
4. **Mobile Height**: 4.5cm - 41.94cm
5. **AI Lens**: Binary (0/1)

### Categorical Features
1. **Model**: Phone model name
2. **Colour**: Phone color variants
3. **Rear Camera**: Camera specifications
4. **Front Camera**: Front camera specs
5. **Processor**: Processor brand/model

---

## ⭐ Feature Importance Rankings

Based on F-Regression scores and model feature importance:

| Rank | Feature | F-Score | Correlation | Impact Level |
|------|---------|---------|-------------|--------------|
| 1 | **Memory (Storage)** | 254.94 | +0.567 | 🔥 Highest |
| 2 | **RAM** | 212.80 | +0.532 | 🔥 Very High |
| 3 | Mobile Height | 17.23 | +0.176 | Moderate |
| 4 | AI Lens | 13.04 | -0.154 | Low |
| 5 | Battery Capacity | 0.63 | -0.034 | Minimal |

### Key Insights:
- **Memory and RAM** are by far the strongest predictors of price
- **Battery capacity** has surprisingly minimal impact on pricing
- **AI Lens** shows slight negative correlation (possibly due to market positioning)

---

## 🤖 Model Performance Comparison

### Models Tested
8 different regression models were trained and evaluated:

| Model | R² Score | RMSE (₹) | MAE (₹) | Rank |
|-------|----------|----------|---------|------|
| **Gradient Boosting** ⭐ | **0.8484** | **4,571** | **2,349** | 🥇 1st |
| Linear Regression | 0.8374 | 4,734 | 1,810 | 🥈 2nd |
| Random Forest | 0.8331 | 4,796 | 1,798 | 🥉 3rd |
| Ridge Regression | 0.8252 | 4,908 | 2,021 | 4th |
| Decision Tree | 0.7237 | 6,171 | 1,281 | 5th |
| Lasso | 0.7143 | 6,275 | 1,759 | 6th |
| KNN | 0.6908 | 6,528 | 2,478 | 7th |
| SVR | -0.0178 | 11,844 | 6,964 | 8th |

### Best Model: Gradient Boosting
- **Accuracy**: 84.84% (R²)
- **Average Error**: ₹2,349
- **Optimal Parameters**:
  - Learning Rate: 0.05
  - Max Depth: 4
  - N_Estimators: 200

---

## 📊 Data Distribution Insights

### Price Distribution
- **Skewness**: 2.43 (Strong right skew)
- **Interpretation**: Few expensive phones dominate the high-end market
- **Most Common Range**: ₹9,000 - ₹19,000

### Feature Distributions
- **Memory**: Most phones have 128GB (median)
- **RAM**: 6GB is most common
- **Battery**: 5000mAh is standard
- **Outliers**: Several premium phones above ₹50,000

---

## 💡 Detailed Feature Impact Analysis

### 1. Memory (Storage) - Highest Impact ⭐⭐⭐⭐⭐
**Impact Score: 254.94 | Correlation: +0.567**

- **256GB**: Premium segment (₹25,000+)
- **128GB**: Mid-range sweet spot (₹12,000-₹20,000)
- **64GB**: Budget segment (₹7,000-₹12,000)
- **32GB and below**: Entry-level (< ₹7,000)

**Key Finding**: Every doubling of storage adds approximately ₹3,000-₹5,000 to the price.

### 2. RAM - Second Highest Impact ⭐⭐⭐⭐⭐
**Impact Score: 212.80 | Correlation: +0.532**

- **8GB**: Premium phones (₹20,000+)
- **6GB**: Mid-range standard (₹12,000-₹18,000)
- **4GB**: Budget-friendly (₹8,000-₹12,000)
- **2GB**: Entry-level (< ₹8,000)

**Key Finding**: RAM upgrade from 4GB to 8GB adds approximately ₹4,000-₹6,000.

### 3. Mobile Height - Moderate Impact ⭐⭐
**Impact Score: 17.23 | Correlation: +0.176**

- Larger phones tend to be slightly more expensive
- Correlation is weak but positive
- Likely proxy for screen size

### 4. AI Lens - Low Impact ⭐
**Impact Score: 13.04 | Correlation: -0.154**

- Only 6.3% of phones have AI lens
- Slight negative correlation (surprising finding)
- May indicate budget phones adding AI as marketing feature

### 5. Battery Capacity - Minimal Impact ⭐
**Impact Score: 0.63 | Correlation: -0.034**

- **Surprising Finding**: Battery has almost no impact on price
- Most phones standardized at 5000mAh
- Manufacturers don't charge premium for larger batteries

---

## 🎯 Model Training Process

### Data Preprocessing
1. **Missing Values**: None detected
2. **Feature Engineering**:
   - Extracted numeric values from text columns (RAM, Memory, Battery)
   - Created separate numeric features
3. **Encoding**:
   - Numeric features: StandardScaler
   - Categorical features: OneHotEncoder
4. **Train-Test Split**: 80-20 split (432 train, 109 test)

### Hyperparameter Tuning
- **Method**: GridSearchCV with 3-fold cross-validation
- **Best Model**: Gradient Boosting
- **Validation R²**: 0.778

---

## ✅ Key Conclusions

### Technical Findings
1. **Memory is King**: Storage capacity is the #1 price determinant
2. **RAM Matters**: Second most important feature for pricing
3. **Battery Surprise**: Battery capacity has minimal price impact
4. **Model Accuracy**: Gradient Boosting achieved 84.84% accuracy
5. **Prediction Error**: Average error of ₹2,349 is acceptable for business use

### Business Insights
1. **Market Segmentation**:
   - Budget: < ₹10,000 (2-4GB RAM, 32-64GB storage)
   - Mid-range: ₹10,000-₹20,000 (4-6GB RAM, 64-128GB storage)
   - Premium: > ₹20,000 (6-8GB RAM, 128-256GB storage)

2. **Pricing Strategy**:
   - Memory and RAM upgrades justify significant price increases
   - Battery capacity can be optimized for cost without affecting price
   - Camera specifications have moderate impact

3. **Consumer Behavior**:
   - Buyers prioritize storage and RAM over battery
   - Sweet spot: 128GB/6GB configuration at ₹13,000-₹16,000

---

## 💼 Recommendations

### For Manufacturers
1. **Focus on memory and RAM** for premium positioning
2. **Optimal mid-range config**: 128GB/6GB
3. **Battery optimization**: Can reduce costs without price impact
4. **AI features**: Don't command premium pricing yet

### For Consumers
1. **Prioritize storage and RAM** when buying
2. **Don't overpay** for battery capacity alone
3. **Best value**: ₹13,000-₹16,000 range
4. **Future-proofing**: Invest in 128GB+ storage

### For Retailers
1. **Stock more** 128GB/6GB configurations
2. **Use predictions** for inventory management
3. **Marketing focus**: Emphasize memory/RAM specs
4. **Pricing strategy**: Use model for competitive pricing

---

## 📈 Future Improvements

### Model Enhancements
1. **Feature Engineering**:
   - Add brand reputation scores
   - Include launch date/age of phone
   - Add market segment indicators

2. **Advanced Models**:
   - Neural networks for non-linear patterns
   - Ensemble methods combining multiple models
   - Time-series analysis for price trends

3. **Data Collection**:
   - Expand dataset to 1000+ phones
   - Include more brands and models
   - Add customer reviews/ratings

### Business Applications
1. **Dynamic Pricing**: Real-time price recommendations
2. **Inventory Optimization**: Predict demand by price point
3. **Competitive Analysis**: Compare pricing strategies
4. **Market Segmentation**: Identify underserved segments

---

## 📁 Project Deliverables

### Files Generated
1. **mobile_price_presentation.html**: Interactive presentation
2. **feature_importance.png**: Feature importance visualization
3. **feature_importances.csv**: Detailed importance scores
4. **selectk_scores.csv**: Feature selection scores
5. **sample_processed_features.csv**: Processed data sample

### Code Artifacts
- Complete EDA pipeline
- 8 trained ML models
- Preprocessing pipeline
- Hyperparameter tuning results

---

## 🎓 Technical Stack

- **Language**: Python 3.13
- **Libraries**:
  - pandas, numpy: Data manipulation
  - matplotlib, seaborn: Visualization
  - scikit-learn: Machine learning
  - XGBoost: Gradient boosting (optional)

---

## 📞 Contact & Questions

For questions or further analysis, please refer to:
- Jupyter Notebook: `Mobile data price prediction.ipynb`
- Output Directory: `./mobile_price_output/`
- Presentation: `mobile_price_presentation.html`

---

**Project Completed**: Successfully analyzed 541 mobile phones with 8 ML models
**Best Model**: Gradient Boosting (R² = 0.8484, MAE = ₹2,349)
**Key Finding**: Memory and RAM are the dominant price factors

---

*End of Summary*
