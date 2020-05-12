# Expiration-day-effects-BTC

***Study of expiration days effects for CME bitcoin futures

***Import the daily data into RStudio with the following code using daily data.csv:

library(readr)
daily_data <- read_csv("~/Desktop/daily_data.csv", 
    col_types = cols(`2day_Return` = col_number(), 
        `7day_return` = col_number(), Daily_Volatility = col_number(), 
        Daily_return = col_number(), Date = col_date(format = "%m/%d/%Y"), 
        PriceUSD = col_number(), SettlementDay = col_number()))
View(daily_data)

***Test for differences in returns/volatility for expiration days:

wilcox.test(daily_data$Daily_return, daily_data$SettlementDay, paired=FALSE)

wilcox.test(daily_data$Daily_Volatility, daily_data$SettlementDay, paired=FALSE)

***Import 4-hour data into RStudio with the following code using X4hour data.csv:

library(readr)
X4hour_data <- read_csv("Desktop/4hour data.csv", 
    col_types = cols(`24-hour return` = col_number(), 
        `48-hour return` = col_number(), 
        `72-hour return` = col_number(), 
        close = col_number(), date = col_date(format = "%m/%d/%Y"), 
        high = col_number(), low = col_number(), 
        open = col_number(), pricechange = col_number(), 
        settlement = col_number(), `time (London: GMT/BST)` = col_time(format = "%H:%M"), 
        volatility = col_number()))
View(X4hour_data)

***Test for differences in returns for 4-hours up to expiration versus other 4-hour trading sessions:

wilcox.test(X4hour_data$pricechange, X4hour_data$settlement, paired=FALSE)


***Test for differences in the 24-hour/48-hour/72-hour returns at time of expiration:

wilcox.test(X4hour_data$24-hour_return, X4hour_data$settlement, paired=FALSE)

wilcox.test(X4hour_data$48-hour_return, X4hour_data$settlement, paired=FALSE)

wilcox.test(X4hour_data$72-hour_return, X4hour_data$settlement, paired=FALSE)

***Test for differences in volatility for 4 hours up to expiration:

wilcox.test(X4hour_data$volatility, X4hour_data$settlement, paired=FALSE)


***Import 4-hour data for Fridays only with Fridays.csv file:

library(readr)
Fridays <- read_csv("Desktop/Fridays.csv", 
    col_types = cols(`24-hour return` = col_number(), 
        `48-hour return` = col_number(), 
        `72-hour return` = col_number(), 
        close = col_number(), date = col_date(format = "%d/%m/%Y"), 
        high = col_number(), low = col_number(), 
        open = col_number(), pricechange = col_number(), 
        settlement = col_number(), `time (London: GMT/BST)` = col_time(format = "%H:%M"), 
        volatility = col_number()))
View(Fridays)


***Test for differences in returns/volatility for expiration Fridays versus non-expiration Fridays:

wilcox.test(Fridays$24-hour_return, Fridays$settlement, paired=FALSE)

wilcox.test(Fridays$48-hour_return, Fridays$settlement, paired=FALSE)

wilcox.test(Fridays$72-hour_return, Fridays$settlement, paired=FALSE)


***Test for differences in volatility for 4 hours up to expiration:

wilcox.test(Fridays$volatility, Fridays$settlement, paired=FALSE)
