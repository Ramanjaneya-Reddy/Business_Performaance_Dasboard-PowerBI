# Business_Performaance_Dasboard-PowerBI

This is a Power BI project on how to create an end to end dashboard within Power BI software for finance business to visualize business related KPIs and visualizations. This dashboard covers a lot of key dashboard design and development techniques of Power BI. Some of the key topics are professional dashboard design, yoy performance metrics, conditional formatting, dax expression for trend comparison and finally a lot of formatting of KPIs, table, line chart, bar chart, slicer and overall dashboard background for a professional look and feel. This Power BI KPI performance dashboard is developed from scratch with the finance dataset.


DAX Queries used

1.  Sales YoY% 
[ Sales YoY%] = 
IF(
	ISFILTERED('financials'[Date]),
	ERROR("Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column."),
	VAR __PREV_YEAR =
		CALCULATE(
			SUM('financials'[ Sales]),
			DATEADD('financials'[Date].[Date], -1, YEAR)
		)
	RETURN
		DIVIDE(SUM('financials'[ Sales]) - __PREV_YEAR, __PREV_YEAR)
)


2.  COGS YoY%
COGS YoY% = 
IF(
	ISFILTERED('financials'[Date]),
	ERROR("Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column."),
	VAR __PREV_YEAR =
		CALCULATE(
			SUM('financials'[COGS]),
			DATEADD('financials'[Date].[Date], -1, YEAR)
		)
	RETURN
		DIVIDE(SUM('financials'[COGS]) - __PREV_YEAR, __PREV_YEAR)
)


3.  Gross Sales YoY%
Gross Sales YoY% = 
IF(
	ISFILTERED('financials'[Date]),
	ERROR("Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column."),
	VAR __PREV_YEAR =
		CALCULATE(
			SUM('financials'[Gross Sales]),
			DATEADD('financials'[Date].[Date], -1, YEAR)
		)
	RETURN
		DIVIDE(SUM('financials'[Gross Sales]) - __PREV_YEAR, __PREV_YEAR)
)



4.  Profit YoY%
Profit YoY% = 
IF(
	ISFILTERED('financials'[Date]),
	ERROR("Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column."),
	VAR __PREV_YEAR =
		CALCULATE(
			SUM('financials'[Profit]),
			DATEADD('financials'[Date].[Date], -1, YEAR)
		)
	RETURN
		DIVIDE(SUM('financials'[Profit]) - __PREV_YEAR, __PREV_YEAR)
)


5.  Sales 2013
Sales 2013 = CALCULATE(SUM(financials[ Sales]), YEAR(financials[Date]) = 2013)


6.  Sales 2014
Sales 2014 = CALCULATE(SUM(financials[ Sales]), YEAR(financials[Date]) = 2014)
