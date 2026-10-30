# Superstore Retail Sales: Exploratory Data Analysis

## Executive Summary
I analyzed 9,994 order line items (about 5,000 orders) from a US retail chain between January 2015 and December 2018, covering $2.30M in sales and $286K in profit (a 12.5% margin). The analysis shows that profit is held back mainly by deep discounting and by the Furniture category, not by customer type. Discounts above 20% apply to only 14% of line items but lose about $135K, erasing roughly a third of the profit earned on all other sales.

## Business Problem
Management wants to know where the business makes and loses money. I set out to answer four questions: how purchase volume is distributed across customer segments, how sales change by month and season, which categories and regions drive revenue and profit, and how sensitive profit is to discounting.

## Methodology
**Data wrangling.** The CSV contained the People and Returns sheets of the original workbook stacked beneath the orders, which left 806 rows with no order data. I separated them into their own tables and kept the 9,994 real order rows. I then profiled missing values, filled the 11 missing postal codes (all Burlington, Vermont) using the known ZIP code, and stored postal codes as five-digit text.

**Feature preparation.** I converted Order Date and Ship Date to datetime with an explicit month/day/year format, confirmed that no order shipped before it was placed, and extracted Year, Month and Year-Month columns.

**Aggregation.** I grouped Sales, Profit, distinct order count, average discount and profit margin by Category, Region and Segment, and built a Region by Category profit pivot. I checked that the grouped totals matched the raw totals exactly.

**Visualization.** I plotted monthly sales, the same months stacked by year to show seasonality, a discount versus profit scatter plot, and average profit by discount level. I also grouped discounts into four bands (none, up to 20%, 21-40%, over 40%) to quantify the effect.

## Skills
Python, Pandas (groupby, pivot tables, datetime handling), Matplotlib, Seaborn, data cleaning and missing-value profiling, exploratory data analysis, business insight communication, Jupyter / Google Colab.

## Results and Business Recommendations
**Discounts above 20% are the biggest profit leak.** Average profit per line item is positive up to a 20% discount and negative from 30% upward. Discounted lines above 20% lose about $135K in total, and those over 40% carry a margin of about -77%. I recommend capping discounts near 20% or requiring approval above it.

**Furniture grows revenue but not profit.** Furniture accounts for 32% of sales ($742K) but only 6% of profit, with a 2.5% margin against about 17% for Technology and Office Supplies. I recommend reviewing Furniture pricing and discount rules before pushing more volume.

**The Central region underperforms.** Its margin is 7.9%, roughly half of West's 14.9%, and it has the deepest average discount (24%, and 30% on Furniture). Central Furniture is the only region and category combination that loses money (-$2,871).

**Sales are seasonal and growing.** Each year follows the same shape: weak in January and February, a bump in March, and a strong rise from September to a peak in November and December. November 2018 was the best month at about $118K. I recommend planning inventory, staffing and promotions around this cycle.

**West and Technology are the strongest profit engines.** West earns $108K in profit and Technology earns $145K at a 17.4% margin, so growth investment should start there.

**Customer segment is a weaker lever.** Margins range only from 11.6% (Consumer) to 14.0% (Home Office), a gap of about 2.5 points, compared with about 15 points between categories. Profit improvement should focus on product mix and discount policy rather than on segment targeting.

*Note: these findings show associations in the data and do not prove that discounts cause losses. Some of the loss may come from products and regions that were already low-margin.*

## Next Steps
I would test whether the discount effect holds within each category and region, to separate the impact of discounting from the impact of product mix. I would also look at the Returns data I set aside to see whether returned orders concentrate in particular categories or discount levels, and build a Power BI dashboard so decision makers can explore sales, margin and discount views interactively.