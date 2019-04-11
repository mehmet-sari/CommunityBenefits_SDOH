### Calculation the Cost of Uncompensated Care in HCRIS

Thanks to the [detail instruction of CMS](https://www.costreportdata.com/instructions/Instr_S100.pdf), it is easy to figure out how uncompensated care is calculated in CMS. 
The regular calculation of uncompensated care in the literature is simply the sum of bad debt and charity care. The Cost report data provides Worksheet S-10 that includes data regarding uncompensated care. Here is the definition of uncompensated care (UC) stated in the instruction:

> Uncompensated care consists of charity care, non-Medicare bad debt, and non-reimbursable
Medicare bad debt. Uncompensated care does not include courtesy allowances, discounts given
to patients that do not meet the hospital’s charity care policy, or discounts given to uninsured
patients that do not meet the hospital's FAP, or bad debt reimbursed by Medicare.

Let's look at the [Worksheet S-10 form](https://github.com/msari6/CommunityBenefits_SDOH/blob/master/HCRIS/Instr_S100.pdf) to see what includes regarding UC. 

As we see in the form, Line 20 to Line 31 are related to uncompensated care. Based on the definition and UC calculation in the literature, here is how UC is calculated:

>> UC = Charity Care Costs + Non-Medicare Bad Debt + Non-reimbursable Medicare Bad Debt

It looks like the info we need is in the line 30 which gives us the cost of uncompensated care; however there is one thing that we need to consider. CMS changed the format of HCRIS and also made some minor but important changes in the calculation of some line. For that reason, it is better to see how each line in UC section in the form is calculated. The instruction gives a detailed explanation how hospital/provider needs to put some figures/numbers in each line. Here is the explanation for Line 30:

> -Calculate the cost of uncompensated care by entering the sum of lines 23, column 3, and line 29.

line 23 says it is cost of charity care (Line 21 minus Line 22) and Line 29 says it is the cost of non-Medicare and non-reimbursable Medicare bad debt expense. So far what we have for the calculation is Line 21, Line 22, Line 29. We started from very last line and so let's keep going up. 

For line 29 which is the cost of non-Medicare and non-reimbursable Medicare bad debt expense, the instruction says:

>For cost reporting periods beginning before October 1, 2013, the cost of non-Medicare and non- reimbursable Medicare bad debt expense is calculated by multiplying line 28 by the CCR on line 1.
For cost reporting periods beginning on or after October 1, 2013, the cost of non-Medicare bad
debt expense is calculated by multiplying line 28 by the CCR on line 1. The cost of non- reimbursable Medicare bad debt expense is calculated by subtracting line 27 from line 27.01 (this
amount is not multiplied by the CCR on line 1). 

So we have three extra lines to consider for the UC calculation:  Line 28, Line 27.01, Line 27.

Let's make it more visible:

> UC = Charity Care Costs + Non-Medicare Bad Debt + Non-reimbursable Medicare Bad Debt = Line 30
> 
> UC = Charity Care Costs + Line 29 
> 
> UC = Charity Care Costs + (Line 28 + Line 27.01 - Line 27)
> 

Now it is time to look at Line 28 which is about Non-Medicare Bad Debt to see if it is calculated with other line(s). 

> Line 28--Effective for cost reporting periods beginning before October 1, 2013, calculate the non- Medicare bad debt expense by subtracting line 27 from line 26. Effective for cost reporting periods
beginning on or after October 1, 2013, calculate the non-Medicare bad debt expense by subtracting
line 27.01 from line 26.

Two more lines for the calculation: Line 27.01 and Line 26.

> UC = Charity Care Costs + (Line 26 - Line 27.01) + Line 27.01 - Line 27
> 

The instruction shows that there is no need to consider other line for Line 27.01 and Line 26. The last component that we need to look at is charity care cost. The instruction and form shows that we need to look at line 20-23 to calculate charity cost. My understanding of what costs can be considered as charity care leads me to take Line 23 and use it as charity care cost. What Line 23 does is to substract "payments received from patients for amounts previously written off as charity care" (line 22) from "cost of patients approved for charity care and uninsured discounts" (line 21). 

Let's finalized our little formula with two extra lines.

> UC = Line 21 - Line 22 + (Line 26 - Line 27.01) + Line 27.01 - Line 27
> 
> UC = (Line 21 - Line 22) + (Line 26 - Line 27)
> 
> UC = Charity Care Costs + Bad Debt Costs
> 

The line 26 is the total bad debt expense for the entire hospital complex and the line 27 is Medicare reimbursable bad debts for the entire hospital complex. To substract Line 27 from Line 26 gives us bad debt expense. 

Here is the simply trick to eliminate the change occured on October 1, 2013. Instead of adjusting the data across the year, this simple solution can be used to calculate UC for each year after 2010. 

Let's look at the data to confirm it.









