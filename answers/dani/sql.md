1.  In what state have we issued the most principal? The greatest number of loans?

# most principal (amount_cents)

SELECT state, sum(amount_cents) as total FROM loans
GROUP by state
ORDER by total desc
LIMIT 1;

>> CA, tota = -1494036406  / 100 (cents) = 14940364 (??)

# greatest number of loans

SELECT state, count(*) FROM loans
GROUP by state
ORDER by COUNT DESC
limit 1;

>> CA, loans = 276710

2. In what state have we issued the most principal in WebBank-owned loans? The greatest number of WebBank-owned loans?
?? attribute?


3. How many loans did we issue in September 2014 in the US? In the UK?
? loans? loan contracts? attribt? = funding date?

# FRO
"SELECT COUNT(*) as all_sep FROM loans
WHERE funding_date BETWEEN '2014-09-01' AND '2014-09-30';"

>> 58966

# UK

>> 6495

4. How many customers do we have whose first name starts with the letter S?

SELECT COUNT(*) as s_people FROM people
WHERE first_name LIKE 'S%' 

>> 429502

5. On what date did we break $100MM in total principal funded?
 

run_query_us("SELECT
    funding_date,
    sum(amount_cents / 100) over (order by funding_date rows unbounded preceding) as cum_amount
from loans;
")
 
>> 2014-01-23 for 100M


