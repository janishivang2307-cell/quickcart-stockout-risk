# QuickCart Stockout Risk Prediction

## 📌 Project Overview

This project develops a machine learning classification model to predict **stockout risk** for QuickCart inventory.

The goal is to identify products that are **Safe, At-Risk, or Imminent** so that inventory teams can prioritize products that may require attention.

## 🎯 Business Objective

The project focuses on predicting stockout risk using inventory, store, SKU, supplier, and event information.

The three target classes are:

* **Safe**
* **At-Risk**
* **Imminent**

The project particularly focuses on **recall for the Imminent class**, because identifying potential imminent stockouts is important for inventory planning.

## 📊 Dataset

The project uses the following data sources:

* `dim_stores.csv`
* `dim_skus.csv`
* `dim_suppliers.csv`
* `dim_events.csv`
* `fact_inventory_daily.csv`

The inventory fact table contains **21,600 records**, representing store-SKU-date combinations.

The data covers **October 1, 2026 to October 30, 2026**.

## 🔧 Data Preparation

The project includes:

* Loading the dimension and fact tables
* Joining the dimension tables with the inventory fact table
* Standardizing city names
* Cleaning supplier reliability values
* Handling missing supplier reliability values
* Creating inventory-related features
* Creating temporal features
* Creating a time-based train-test split

### Feature Engineering

Key engineered features include:

* `reorder_gap`
* `days_of_cover_ratio`
* `supplier_reliability_clean`
* `is_recent_reorder`
* `day_of_month`
* `days_since_festival_start`

## 🤖 Models

The following models were evaluated:

1. Majority-Class Baseline
2. Multinomial Logistic Regression
3. Random Forest

A time-based split was used:

* **Training:** October 1–23, 2026
* **Testing:** October 24–30, 2026

## 📈 Model Results

| Model                   |   Accuracy | Imminent Recall |
| ----------------------- | ---------: | --------------: |
| Majority-Class Baseline |     62.28% |               — |
| Logistic Regression     |     92.52% |         **76%** |
| Random Forest           | **93.04%** |             62% |

## 🏆 Model Selection

Random Forest achieved slightly higher overall accuracy.

However, **Logistic Regression achieved higher recall for the Imminent class (**
