To Create new data & print

data test;
input pid age name$ gender$;
datalines;
1 25 arpan f
2 27 karan m
run;

proc print data=test;
run;

TO SAVE LOG

proc printto log="/home/u64263069/faers/today.log";
run;

