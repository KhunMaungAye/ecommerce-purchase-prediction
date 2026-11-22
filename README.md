# Online Shoppers Purchase Prediction

Predicting whether a visitor to an online shop will make a purchase, based on how they browse the website during their session.

## Problem

Most visitors to an online shop leave without buying anything. If a shop can tell during a session which visitors are more likely to buy, then it can act on it, for example by showing a discount to visitors who are very close to deciding.

This project will build a machine learning model that predicts whether a session ends in a purchase (`Revenue = True`).

## Dataset

[Online Shoppers Purchasing Intention Dataset](https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset) from the UCI Machine Learning Repository.

It has:

- 12,330 sessions, each from a different user, over one year
- 17 features (pages visited, time spent, bounce and exit rates, month, visitor type and so on...) and 1 target, `Revenue`
- Only **15.5%** of sessions end in a purchase, so the classes are imbalanced

The dataset is by C. Okan Sakar and Yomi Kastro (2018), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
A copy is included in `Data/online_shoppers_intention.csv`.

## Key findings from data exploration

Full analysis: [`notebooks/01_data_exploration.ipynb`](notebooks/01_data_exploration.ipynb)

- The data has no missing values. The 125 duplicate rows are real one-page bounce visits, so they were kept.
- A model that always predicts "no purchase" would already be 84.5% accurate, so the model will be judged on precision and recall instead of accuracy.
- `PageValues` separates buyers from non-buyers the most (average 27.26 vs 1.98).
- New visitors (24.9%) and November (25.4%) have the highest purchase rates.

## Model results

Full analysis: [`notebooks/02_modelling.ipynb`](notebooks/02_modelling.ipynb)

Results on the test set (20% of sessions, never seen during training), for the buyers class:

| Model                          | Accuracy  | Precision | Recall  | F1       |
| ------------------------------ | --------- | --------- | ------- | -------- |
| Logistic regression            | 88.1%     | 74%       | 36%     | 0.48     |
| Logistic regression (balanced) | 84.1%     | 49%       | 74%     | 0.59     |
| **Random forest (balanced)**   | **89.0%** | **63%**   | **70%** | **0.66** |

- The **balanced random forest** is the final model. It finds **70% of buyers**, and about 2 in 3 of its "will buy" predictions are correct.
- Handling class imbalance mattered more than the choice of model: it roughly doubled recall.
- **Limitation:** the model depends heavily on `PageValues`. Without it, F1 drops from 0.66 to 0.35, so the model works best later in a session, after several pages have been viewed.

## Setup

Requires Python 3.12 or newer. Check your version first:

```bash
python3 --version
```

If it is older than 3.12, install a newer version from
[python.org](https://www.python.org/downloads/) and use it by name
(for example `python3.12` or `python3.13`) instead of `python3` below.

```bash
git clone https://github.com/KhunMaungAye/ecommerce-purchase-prediction.git
cd ecommerce-purchase-prediction
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

These steps are for macOS and Linux. On Windows, see the
[Python venv documentation](https://docs.python.org/3/library/venv.html).

## Project status

This project is still in progress.

- [x] Project setup and Git workflow
- [x] Data exploration
- [x] Model training and evaluation
- [ ] Prediction API
- [ ] Frontend
