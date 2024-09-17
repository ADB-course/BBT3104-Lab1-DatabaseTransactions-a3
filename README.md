[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/r-tQZu0l)
# BBT3104-Lab1of6-DatabaseTransactions


| **Key**                                                               | Value                                                                                                                                                                              |
|---------------|---------------------------------------------------------|
| **Group Name**  A3                                                        | ? |
| **Semester Duration**                                                 | 19<sup>th</sup> August - 25<sup>th</sup> November 2024                                                                                                                       |

## Flowchart
![alt text](<Screenshot 2024-09-17 125148.png>)
## Pseudocode
function processOrder(customerNumber, products) {
  // Start transaction
  startTransaction();

  // Generate new order number
  orderNumber = getNextOrderNumber();

  // Insert order into orders table
  insertOrder(orderNumber, customerNumber);

  // Iterate through products
  for each product in products:
    // Insert order detail into orderdetails table
    insertOrderDetail(orderNumber, product.code, product.quantity, product.price);

    // Update product quantity in stock
    updateProductQuantity(product.code, -product.quantity);

  // Insert payment into payments table
  insertPayment(customerNumber, paymentAmount);

  // Commit transaction
  commitTransaction();
}
## Support for the Sales Departments' Report
1. Create a Payments Table:
If you don't already have one, create a Payments table to record individual payment transactions.
Include columns like paymentID, orderNumber, paymentAmount, paymentDate, and paymentType (e.g., cash, check, credit card).
2. Modify the Orders Table:
Add a totalPaid column to the Orders table to store the cumulative amount paid for each order.
Add a status column to indicate the payment status (e.g., "Fully Paid", "Partially Paid", "Pending").
3. Update the Payments Table:
Whenever a payment is made, update the totalPaid column in the Orders table and insert a new row into the Payments table.
4. Create a View (Optional):
For convenience, create a view that joins the Orders and Payments tables to provide a unified view of order information and payments. This can simplify query writing.