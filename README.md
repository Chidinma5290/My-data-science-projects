 Market Basket Analysis - Applying Megastore Bundling Strategy
The objective of the data analysis is to identify strong product connections and common product pairings across customer segments to create focused product bundles and promotional deals that boost average order value and enhance the overall shopping experience. Therefore, this goal will help Megastores to strategically focus on sales growth, customer behavior insights, and operational improvement.

## Problem Solved
Megastores needed to know which products customers naturally buy together to drive cross-selling. I analyzed a real basket - Order ID 536370 (Inflatable Political Globe, Set 2 Red Retrospot Tea, Panda Sticker Sheet, etc.) - to uncover hidden buying patterns and turn them into bundles.

## My Approach

1. Data Preparation:
- Encoded 4 categorical variables: OrderPriority (Medium=1, High=2) and Satisfaction (0-4) with ordinal encoding; Segment and PaymentMethod with one-hot encoding (Consumer/Corporate, PayPal/Credit Card)
- Transactionalized: Grouped by OrderID and ProductName, unstacked into binary matrix (Rows=Orders, Columns=Products, True/False)
- Created `encoded_dataset.csv` and `transactionalized_dataset.csv`

**2. Model - Apriori Algorithm (mlxtend):**
- Parameters: min_support=0.01 (1%), metric=lift, min_threshold=1.0, use_colnames=True
- Sorted all rules by Lift descending
- Top 3 rules all have Support=1.13%, Confidence=1.0, Lift=88.2 - exceptionally strong

**Top 3 Rules Found:**
- Cluster 1: Childrens Cutlery Dolly Girl + Alarm Clock Bakelike Red + Card Dolly Girl -> Round Snack Boxes Woodland + Cutlery Spaceboy + Alarm Clock Pink + Spaceboy Birthday Card
- Cluster 2: Plasters in Tin Spaceboy and Set6 Red Spotty Paper Cups -> Set6 Red Spotty Plates and  Alarm Clocks , Woodland Snack Boxes added
- Cluster 3 is reverse of Rule 1 (symmetric) - proves Dolly Girl and Spaceboy ranges are bought as a set

**3. Customer Segmentation:**
- Used Segment field (Consumer vs Corporate) to target Consumer segment - most likely buying themed party sets for family use

**4. Business Result:**
- Found 2 themed clusters: Dolly Girl Party Range + Spaceboy/Woodland Party Range
- Lift 88.2 = products bought 88x more than random chance. Confidence 1.0 = 100% reliable
- Recommendation: Create 2 pre-packaged themed bundles, implement "Frequently Bought Together" on website, co-locate Dolly Girl/Spaceboy/Woodland in same aisle to boost Average Order Value

## Tech Stack
Python, Pandas, mlxtend (Apriori, Association Rules), Jupyter Notebook

## Files in this Repo
- ` Apriori Python Script.ipynb` - Main Apriori code
- `encoded_dataset.csv` - Ordinal + one-hot encoded data
- `transactionalized_dataset.csv` - Binary basket matrix for Apriori

## Key Insights
- Lift 88.2 is extremely high (2.0 is already notable) - indicates customers treat these as coordinated party gift sets
- Support 1.13% = 1 in 100 orders - commercially meaningful in large retail catalog
- Perfect Confidence 1.0 means bundling recommendation will never fail

## Author
Chidinma5290 - Data Analyst/ Science 
