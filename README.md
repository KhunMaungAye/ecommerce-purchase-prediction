# Online Shoppers Purchase Prediction

Predicting whether a visitor to an online shop will make a purchase, based on how they browse the website during their session.

## Problem

Most visitors to an online shop leave without buying anything. If a shop can tell during a session which visitors are more likely to buy, then it can act on it, for example by showing a discount to visitors who are very close to deciding.

This project will build a machine learing model that predicts whether a session ends in a purchase (`Revenue = True`).

## Dataset

[Online Shoppers Purchasing Intention Dataset](https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset) from the UCI Machine Learning Repository.

It has:

- 12,330 sessions, each from a different user, over one year
- 17 features (pages visited, time spent, bounce and exit rates, month, visitor, type and so on...) and 1 target, `Revenue`
- Only **15.5%** of sessions end in a purchase, so the classes are imbalanced

The dataset is by C. Okan Sakar and Yomi Kastro (2018), licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
A copy is included in `Data/online_shoppers_intention.csv`

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

On Windows, use `py -3.12 -m venv .venv` to create the environment
and `.venv\Scripts\activate` to activate it.

## Project status

This project is still in progress.

- [x] Project setup and Git workflow
- [ ] Data exploration
- [ ] Model training and evaluation
- [ ] Prediction API
- [ ] Frontend
