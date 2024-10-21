

2024-08-15 13:41

Status:

Tags: Missing Data

## Missing Data

lets say we have a jig puzzle 
![[Pasted image 20240815134208.png|300]]
 and a cat mr. pickles
 ![[Pasted image 20240815134347.png|100]]

$Y_i$ : vector of $p$ variables for unit i (a single piece)
$R_i$ : missing data indicator
$Y_{i}=(Y_{i,o},Y_{i,m})$ o - observed, m - missing
### Missing Completely At random(MCAR) 
on the 1st day Mr. Pickles removed pieces at random.

![[Pasted image 20240815134757.png|300]]

Missingness is independent on the data:
$P(R_{i}|Y_i)=P(R_i)$

proportion of the color is maintained

### Missing At random(MAR)

on the 2nd day Mr. Pickels removed more outside pieces 
![[Pasted image 20240815135155.png|300]]

Missingness depends only on the observed data
$P(R_i|Y_i)=P(R_i|Y_{i,o})$

### Missing Not At Random(MNAR)

on the 3rd day Mr. Pickles removed the wings
![[Pasted image 20240815140626.png|300]]

Missingness depends on the missing data

$P(R_i|Y_{i})\neq P(R_i|Y_{i,o})$

### Examples

we have a device that records steps.

scenarios:
1. battery is dead.
	1. that  might be MCAR
	2. but if the battery is gone dead at the evening it can be MAR
2. people don't wear the device because they are lazy.
	1. might be MNAR
	2. if people are lazy on bad weather days that might be MAR


## References

[Missing Data Assumptions](https://www.youtube.com/watch?v=YpqUbirqFxQ)


