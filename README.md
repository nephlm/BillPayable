# BillPayable

## Tools

* Plaid
* AWS
  * SES
  * Lambda   
  * Texteract (Expense)


## ETL Pipeline

* Paperless bills to personal email
* gmail rule to foward to SES email address
* SES to SQS
* SQS to Texteract
  * Texteract output to S3
  * Raw bill to S3
  * ouptut to lambda
    * Key values extracted and written to model 
      * (DynamoDB maybe, it's in the free teir, or maybe just S3 or noDB)
    * Summary Message composed 
      *  To SQS -> SES   

Once complete we should have:

* Raw Bill
* Key/Values of important model data
* Handy summary in email 

## Models

* Payer
* Bill
* Transactions

## Other

* Weekly Bill pay prompt with summary inofrmation:
  * Payer
    * Due Date
    * Amounts Due (min, total)
    * Last paid Date
    * Last paid Amount
    * Link to online Bill, s3 bill, extracted data file
  * Link to 
    * Bill pay interface
    * Checking account transactions
    * Credit Card Transactions

## Packages

* plaid wrapper to get transactions
* texteract wrapper to do payer and field identification.
* reconciliation 
  * match transactions to bills
* model wrappers?
* Local cache of cloud stores data.
