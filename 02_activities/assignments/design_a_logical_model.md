# Assignment 1: Design a Logical Model

## Question 1
Create a logical model for a small bookstore. 📚

At the minimum it should have employee, order, sales, customer, and book entities (tables). Determine sensible column and table design based on what you know about these concepts. Keep it simple, but work out sensible relationships to keep tables reasonably sized. Include a date table. There are several tools online you can use, I'd recommend [_Draw.io_](https://www.drawio.com/) or [_LucidChart_](https://www.lucidchart.com/pages/).

![Assignment_Q1](https://github.com/user-attachments/assets/acea6c95-b0a8-41d7-8942-8d73ccba8a51)

## Question 2
We want to create employee shifts, splitting up the day into morning and evening. Add this to the ERD.

![Assignment_Q2](https://github.com/user-attachments/assets/64b743e4-d746-4d8b-ae9a-61a6b015db55)

## Question 3
The store wants to keep customer addresses. Propose two architectures for the CUSTOMER_ADDRESS table, one that will retain changes, and another that will overwrite. Which is type 1, which is type 2?

_Hint, search type 1 vs type 2 slowly changing dimensions._

Bonus: Are there privacy implications to this, why or why not?
```
Your answer...
```

Type 1: Overwriting customer addresses - when a customer updates the address, the new address will overwrite the old address. There is no historical data of the old address. 

CUSTOMER_ADDRESS table structure:
- CustomerID (PK)
- Street
- City
- Province
- Postal Code
- Country

Privacy Implication:
- Lower Maintenance: lower data volume due to only current address is stored in the system.
- Lower risk: less sensitive data will be exposed if there is a data breach.
- Ease of Compliance: Compliance with data protection may be simpler as less data to manage.
- Customer Service: If a customer submits a dispute related to shipping charges to the old address, it will take more effort to resolve the dispute.
- Customer Consent: Obtaining customer consent may be more straightforward as only one address is collected and stored.


Type2: Retaining changes of customer addresses - when a customer updates the address, the new record for the new address will be created in the table. 

CUSTOMER_ADDRESS table structure:
- AddressID (PK)
- CustomerID (FK)
- Street
- City
- Province
- Postal Code
- Country
- StartDate
- EndDate

Privacy Implication:
- Higher Maintenance: higher data volume due to storing old addresses
- Higher Risk: more sensitive data will be exposed if there is a data breach
- Complex Compliance: Security measures to protect all versions of the address data are needed.
- Customer Service: If a customer submits a dispute related to shipping charges to the old address, it will shorten the time to resolve the dispute as the historical data is stored in the system.
- Customer Consent: Obtaining customer consent for the use of historical address data may be crucial as customers should understand how their past data may be used.

## Question 4
Review the AdventureWorks Schema [here](https://i.stack.imgur.com/LMu4W.gif)

Highlight at least two differences between it and your ERD. Would you change anything in yours?
```
Your answer...
```

Differences:

AdventureWorks Schema:  
- It has more complex relationships. There are many-to-many associations.
- It uses primary keys (PK), foreign keys (FK) to demonstrate the relationships, and also uses unique constraints (U) to ensures that all values in a column are distinct.
- It covers several business domains using different schema, such as Sales, Purchasing, Person, production, human resources and DBO.
- It is structured for a larger and complex business.
- It captures a more detailed view of the entire business and provides a full-fledged data management system. 
 
My ERD: 
- It is more straightforward with one-to-many relationships.
- It is more simple with only primary keys (PK) and foreign keys (FK).
- It focused only on sales related activities such as customers, orders, books, and employees.
- The main purpose is to track transactions and customers.
- It is designed for a small bookstore. Most of the data is transactional. 

Changes to my ERD:
- When my bookstore starts dealing with more vendors, I would want to add a purchasing schema to manage all the vendors and purchase orders.
- I would also want to enhance my customer schemas to track the customer demographics such as adding age and loyalty reward program.
- When my bookstore has more employees, I would want to have a human resources schema to manage the employees.


# Criteria

[Assignment Rubric](./assignment_rubric.md)

# Submission Information

🚨 **Please review our [Assignment Submission Guide](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md)** 🚨 for detailed instructions on how to format, branch, and submit your work. Following these guidelines is crucial for your submissions to be evaluated correctly.

### Submission Parameters:
* Submission Due Date: `September 28, 2024`
* The branch name for your repo should be: `model-design`
* What to submit for this assignment:
    * This markdown (design_a_logical_model.md) should be populated.
    * Two Entity-Relationship Diagrams (preferably in a pdf, jpeg, png format).
* What the pull request link should look like for this assignment: `https://github.com/<your_github_username>/sql/pull/<pr_id>`
    * Open a private window in your browser. Copy and paste the link to your pull request into the address bar. Make sure you can see your pull request properly. This helps the technical facilitator and learning support staff review your submission easily.

Checklist:
- [ ] Create a branch called `model-design`.
- [ ] Ensure that the repository is public.
- [ ] Review [the PR description guidelines](https://github.com/UofT-DSI/onboarding/blob/main/onboarding_documents/submissions.md#guidelines-for-pull-request-descriptions) and adhere to them.
- [ ] Verify that the link is accessible in a private browser window.

If you encounter any difficulties or have questions, please don't hesitate to reach out to our team via our Slack at `#cohort-4-help`. Our Technical Facilitators and Learning Support staff are here to help you navigate any challenges.
