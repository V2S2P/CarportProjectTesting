# CarportProjectTesting
Repo to test things before they get commited to main carport repo
1. In Order entity class, instead of just giving it a userId instance variable, we give it an entire User object so that when we in front end need to get an order we can see the User/customer as well, instead of just their id. We do the same in OrderItem, instead of giving just the orderId and productVariantId, we give it the entire object (Order order, ProductVariant productVariant).

2. If I want to test the a mapper method that is using the view list we made in the database, I believe the test database also needs the exact same constraints.

3. Not able to test insertOrderItems or getOrderItemsByOrderId for now.

4. The way to get orderId to use in the getOrderItemsByOrderId method, we can do this. When the customer has placed an order, we call:
	Order insertedOrder = OrderMapper.insertOrder(order, connectionPool);
The insertOrder method returns a newly created Order object with the generated orderId (from the RETURN_GENERATED_KEYS).
After that we do this:
	int orderId = insertedOrder.getOrderId();
	List<OrderItem> items = OrderMapper.getOrderItemsByOrderId(orderId, connectionPool);

5. Do we need a mapper method for each product we have in the database when we know the length of the carport and need to retrieve the correct variant of the product (rem, spær, stolpe)? Can it be done in a more efficient way?

6. How do we seperate the mapper method usages so we don't use too many mapper methods in one single controller method?

7. Do we use a ProductMapper like Jon? 

8. Is product_description table needed?
