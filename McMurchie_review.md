# Elizabeth McMurchie suggestions for Tyler Foster's R project
### Specific errors
- Line 500 has a code-breaking error "`Error in check_breaks_labels(breaks, labels) : object 'percent' not found`". This may be due to not having all the packages that you need in your libraries. I checked my libraries and all libraries you listed are installed and loaded. The same issue comes up in line 509's chunk of code, as well as line 546's chunk.

### Warnings
- You got a warningabout using `melt()` several places. Melt is part of the `reshape2` package, which has been deprecated. Typically, `pivot_longer()` is preferred to `melt()`, especially if you're using tidyverse. 
- It's probably okay that you have NAs introduced by coercion here but you might want to investigate why that is (it seems to me it's just because you're running an `as.numeric()` on something that isn't always numeric - chromosome position, which is sometimes unknown or muliple)
- Possibly a similar warning in chunk starting line 457, where lines are removed for containing nonfinite values. 

### Suggestions
- Your chromosome disribution graphs are a bit hard to compare. it may help to make two graphs side-by-side or one above the other. A histogram with several bins may be easier to read than the dot distribution you used, too (although that's personal preference).
- It may be helpful to have R print your files into directories using `ggsave("./directory_name/plot_name.png", plot = plot_name etc.)` for the sake of organization. 
- Say "knit" (the ball of thread and knitting needles on R studio above your script window) to make an HTML document that can be pushed online and easily read. 
- I'm sure there's a good way to write loops for what you did in line 145 onward. You could possibly run the `as.numeric()` and `arrange()` steps separately, each with its own loop.

### General comments
- Looks good overall! The most severe issue is the graphs not printing due to the issue with "percent". This prevents the code from completing. However, the graphs look great!