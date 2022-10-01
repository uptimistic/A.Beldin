# A.Beldin

```python

# This python script is programmed to execute the following algorithm
#(subject to modification)
#Note make sure invoice colum is sorted if not already
import copy # this uses the copy module to clone deep copy version
"""
1. Given a column of invoice numbers.

2. Each invoice number has a number of corresponding date(s)

3. Some of the invoice numbers have  just 1 corresponding date.
Others have 2,3,4,5,6,7 dates.

4. For each invoice number only two dates are desired( beginning and end date)-
( can we name what the initial and ends dates should be ?)

5. If the invoice number has just one corresponding date
: - that date serves as both the initial and end date

6. If the invoice number has exactly two corresponding dates :
- the first date serves as the initial and 2nd date is the end date

7 if the invoice number has more than 2 corresponding dates:
-1st date serves as initial.( this can change)
-reception date is the second date ( the program can modify this if its the 3rd or 4th etc )
- this reception date is repeated for the rest of the invoice dates
(3,4,5,6, 7 depending on how many times repeated )
"""
dates =['invoice1date1','invoice2date1','invoice2date2','invoice3date1','invoice3date2','invoice3date3','invoice4date1','invoice4date2','invoice4date3','invoice4date4','invoice5date1','invoice5date2','invoice5date3','invoice5date4','invoice5date5','invoice6date1','invoice6date2','invoice6date3','invoice6date4','invoice6date5','invoice6date6','invoice7date1','invoice7date2','invoice7date3','invoice7date4','invoice7date5','invoice7date6','invoice7date7','invoice8date1']
# dates = ['date1','date1','date2','date1','date2','date3','date1','date2','date3','date4','date1','date2','date3','date4','date5','date1','date2','date3','date4','date5','date6','date1','date2','date3','date4','date5','date6','date7','date8']
invoices = ['invoice1','invoice2','invoice2','invoice3','invoice3','invoice3','invoice4','invoice4','invoice4','invoice4','invoice5','invoice5','invoice5','invoice5','invoice5','invoice6','invoice6','invoice6','invoice6','invoice6','invoice6','invoice7','invoice7','invoice7','invoice7','invoice7','invoice7','invoice7','invoice8']
# fixedDates = [0] * len(dates)
fixedDates = copy.deepcopy(dates)
end_date_position = 2 # this can be modified to 3 or 4

print('equal dates and invoices rows?:' ,len(dates) == len(invoices))
# print code above prints a boolean test to ensure
# number of invoice and date rows are same


uniqueInvoiceList = sorted(list(set(invoices)))
# uniqueInvoices code above finds unique invoices

print('unique invoice list :', uniqueInvoiceList)
invoiceCountList=[]
RowCount = 0
# initialDate =''
# finalDate = ''

for eachUniqueInvoice in uniqueInvoiceList:

    eachCount = invoices.count(eachUniqueInvoice)

    invoiceCountList.append(eachCount)


# this is a print test that can be suppressed
print(invoiceCountList)# this is a print test that can be suppressed


# this is a print test that can be suppressed
invoiceCountPair = zip(uniqueInvoiceList, invoiceCountList)

for eachtuple in invoiceCountPair:
    print(eachtuple)

for eachCount in invoiceCountList:

    RowCount = RowCount + eachCount

    rowIndex = range((RowCount-eachCount),RowCount)

    if eachCount <= 2 :

        for stepIndex in range(eachCount):

            fixedDates[rowIndex[stepIndex]] = dates[rowIndex[stepIndex]]

    elif eachCount > 2 :

        fixedDates[rowIndex[0]] = dates[rowIndex[0]]

        for stepIndex in range(1,eachCount):

            fixedDates[rowIndex[stepIndex]] = dates[rowIndex[(end_date_position-1)]]







#     rowIndex = RowCount+eachCount-1  # 01[2] for 3 , 012[3] for 4 etc
#
#     if eachCount <= 2 :
#
#         fixedDates[rowIndex]=dates[rowIndex]
#
#     else:
#
#         for i in range(1):
#
#             fixedDates[rowIndex]=dates[rowIndex]
#
#         for i in range(1,eachCount):
#
#             fixedDates[rowIndex]=dates[RowCount+end_date_position-1]
#
#     RowCount = RowCount + eachCount
#
finalOutput = zip(invoices, fixedDates)

# THIS LOOP PRINT IS FOR TERMINAL VIEW OR DESKTOP VIEW
for eachtuple in finalOutput:
    print(eachtuple)

# THIS LOOP PRINTS IS WRITE THE OUTPUT TO FILE(same location code is running )

df=open('beldinAngela.txt','w')

df.write('Print of all invoices and corresponding dates ')

for i in finalOutput:
    df.write(str(i))
    df.write('\n')

df.close()


# THIS LOOP ALSO PRINTS IS WRITE THE OUTPUT TO FILE(same location code is running )

def prettyprint(finalOutput):

    with open("beldinAngela.txt",'w') as fileObject:

        fileObject.write('Print of all invoices and corresponding dates ')

        for i in finalOutput:
            fileObject.write(str(i))
            fileObject.write('\n')

prettyprint(finalOutput)


# print("finally we have :" , finalOutput)

#
#
#
#

    # print('{} has {} appearances').format(eachUniqueInvoice,eachCount)

#
# for eachUniqueInvoice in uniqueInvoiceList:
#
#     eachCount = uniqueInvoiceList.count(eachUniqueInvoice)
#
#     RowCount = RowCount + eachCount
#
#     if eachCount == 1:

```
