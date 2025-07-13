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

TO READ EXISTING DATASET AND USE (KEEP,DROP) OPTION

LIBNAME faers "/home/u64263069/faers";

data test;
set faers.all_in_one;
run;

data test;
set faers.all_in_one (keep=primaryid age sex);
run;

data test;
set faers.all_in_one (drop=caseid drug_rec_act drugname_clean);
run;

TO SAVE THIS NEW FILE FILTERED FILE 

data faers.all_in_newone;
set test;
run;

TO USE RENAME,WHERE,LABEL OPTION

data abc;
set faers.all_in_one(RENAME=(drugname=drug));
run;

data abc;
set faers.all_in_one (where=(drugname="INCLISIRAN"));
run;

data abc (label="fda_data");
SET faers.all_in_one;
run;

USING IF 
data abc_new;
    set faers.all_in_one;
    if _N_ = 3 then output;
run;

MAKING NEW DATA AND THEN MERGE 

data x;
input sno name$ age gender$;
cards;
1 karan 27 m
2 arpan 25 f
;
run;

data y;
input sno name$ age gender$;
cards;
3 mishra 24 m
4 janvi 20 f
;
run;

data aa;
set x y ;
run;

proc print data=aa;
run;




