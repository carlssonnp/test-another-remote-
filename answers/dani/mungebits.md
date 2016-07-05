COLUMNS
1. 

med_impute <- column_transformation(function(x) {
    x[is.na(x)] <- median(x, na.rm = TRUE)
    x
})

#med_impute(iris2, 1: 4)

2. 

??question
feeder <- column_transformation(function(feed) {
  factor(ifelse(feed %in% c('horsebean', 'soybean'), 'bean',
         ifelse(feed %in% c('sunflower', 'linseed'), 'seed', 'other')))
})

3. why doesn't this work?

na_outliers <- column_transformation(function(col, min, max) {
	col[which(col > max | col < min)] = NA
})

ROWS
1. filter_rows <- function(dataframe, condition)
  eval.parent(substitute(dataframe <- dataframe[apply(dataframe, 1, condition), ]))

  filter_rows(chickwts, function(x) x[2] != "casein")

OR 

	filter_rows <- function(dataframe, col, pattern)
		dataframe[!dataframe$col == pattern]


MULTI COLUMN

1. 
 con <-multi_column_transformation(function(x, y, s) paste(x, y, sep= s)
 con(df, 1:2, s=".", "final")

 DATA FRAME
 1. Whether we'd like to order a df by column names or by values of elements, we can use functions like order  and arrange, so these are just row / col transformations.

 2. remove_missings violates DRY, so instead of taking the entire df, we could break down the code into a function that generalizes the code to computes if a row or col has more than 20% NA values. Then we can apply this function to the df, specifying if rows or columns.

